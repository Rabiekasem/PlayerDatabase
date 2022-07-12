<svelte:head>
	<title>Players</title>
</svelte:head>

<script>

    import {onMount} from "svelte"
    import Article from "./../components/Article.svelte"
    

    let storage
    let db
    let url= ""
    let playerName = ""
    let playerTeam = ""

    let files = []
    $: file = files[0]

    onMount(
       () => {
           storage = firebase.storage()
           db = firebase.firestore()
       }
    )


    const upload = async () => {
        console.log("trying to upload")
        const sti = storage
          .ref()
          .child("PlayersPictures/" + file.name)
  
          const opplasting = await sti.put(file)
          const urlen = await opplasting.ref.getDownloadURL();
          url = urlen;
   }

   const addName = () => {
       const playerArticle = db.collection("playerSection")
       playerArticle.add({
           playerName,
           playerTeam,
           url
       })
       
       url = ""
       playerName = ""
       playerTeam = ""
   }

   const changeColor = () => {
       document.getElementById("fileInpt").style.color = "black";
   }
  
</script>

<div>
  <div id="divTwo">
    <input id="fileInpt" type="file" bind:files style="color:transparent;" on:change={changeColor}>
    <button id="fileButtonInpt" on:click={upload}>Upload Image</button>
  </div>


  {#if url}

    <form on:submit|preventDefault={addName}>
      <img src={url} alt="image">
      <input bind:value={playerName} placeholder= "Player name">
      <input bind:value={playerTeam} placeholder="Player team">
      <button type="submit" id="picButton">Add</button>
    </form>

  {/if}
</div>

<Article />


<style>

  #divTwo{
      margin-top: 10px;
      display: grid;
  }

   

  #fileButtonInpt {
      width: 250px;
      height: 35px;
      border-radius: 20px;
      background-color: rgba(2, 47, 78, 0.7);
      color: white;
      outline: none;
  }

  #fileButtonInpt:hover {
      background-color: rgba(45, 109, 151, 0.7);
  }

  #fileInpt{
      width: 250px;
      height: 25px;
      padding: 10px 10px;
  }

  input{
      text-align: center;
  }

  form{
      display: grid;
      grid-auto-flow: row;
      justify-content: center;
      align-items: center;
      gap: 5px;
      background-image: linear-gradient(to bottom, rgba(235, 232, 243, 0), rgba(2, 47, 78, 0.2));
      border-radius: 10px;
      box-shadow: 0 0.5px 0.5px 0.5px gray;
      
  }

  div{
      display: grid;
      grid-template-columns: 1fr;
      gap: 10px;
      max-width: 400px;
      margin: auto;
      margin-bottom: 50px;
  }

  img{
      width: 200px;
  }

  #picButton{
      background-color: rgba(45, 109, 151, 0.7);
      border-radius: 5px; 
      color: white;
      height: 30px;
  }

</style>