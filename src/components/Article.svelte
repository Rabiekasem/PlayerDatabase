<script>

    let storage = firebase.storage()
    let db = firebase.firestore()
    const playerArticle = db.collection("playerSection")

    let content = []
    playerArticle.onSnapshot(snap=>{
        content = snap.docs;
    })

</script>


<div id="section">

  {#each content as cont}
    <div>
      <img src={cont.data().url} alt="content">
      <b><p>{cont.data().playerName}</p></b>
      <b><p>{cont.data().playerTeam}</p></b>
    </div>
  {/each}

</div>


<style>

  * {
      font-family: 'Oranienbaum, Poppins, Roboto';
  }      

  #section{
      max-width: 900px; 
      margin: auto auto;
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
      gap: 13px;
      border-right: 1px dashed rgb(209, 200, 200);
      border-left: 1px dashed rgb(209, 200, 200);
         
    }

  #section div {
      background-image: linear-gradient(to bottom, rgba(235, 232, 243, 0.1), rgba(2, 47, 78, 0.1));
      border-radius: 5% 5% 35% 35%;
      box-shadow: 1px 1px 2px 0.5px rgb(141, 180, 245),
                  1px 0 0.5px 0.7px rgb(206, 43, 43);
      width: 170px;
      height: 190px;
      margin: 10px auto;
      transition: 0.7s;
     
  }

  #section div:hover{
      transform: scale(1.2);
      transition: 0.7s;

      box-shadow: 2px 2px 2px 2px rgba(206, 43, 43, 0.7),
                  0.5px 0 0.5px 0.7px rgb(141, 180, 245);
  }


  #section div img {
      width: 100%;
      height: 120px;
      position: relative;
  }

  #section div p {
      text-align: center;
      font-size: 12px;
      position: relative;  
  }

</style>