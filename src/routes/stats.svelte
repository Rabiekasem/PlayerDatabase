<svelte:head>
	<title>Stats</title>
</svelte:head>

<script>

  import {onMount} from "svelte" 
  

  let db
  let nbaData
  let nbaDataTwo
  let EastTeams = []
  let WestTeams = []


  let teamId = ""
  let teamName = ""
  let teamIdTwo= ""
  let teamNameTwo = ""

  onMount(
      async () => {
          db = firebase.firestore()
		  nbaData = await db.collection("nba-data")
		  nbaDataTwo = await db.collection("nba-data-2")
		  nbaData.orderBy("W", "desc")
		  .onSnapshot(snap=>
		    EastTeams = snap.docs
		  )
		  nbaDataTwo.orderBy("W", "desc")
		  .onSnapshot(snap=>
		    WestTeams = snap.docs
		  )
		  
      }
  )

  const addTeam = () =>{
	  nbaData.doc(teamId).set({
		  teamName: teamName,
		  W: 0,
		  L: 0,
		  A: 0,
		  R: 0,
		  S: 0,
		  B: 0,
		  TO: 0
	  })
	  teamName = ""
	  teamId = ""
  }

  const addTeamTwo = () =>{
	  nbaDataTwo.doc(teamIdTwo).set({
		  teamName: teamNameTwo,
		  W: 0,
		  L: 0,
		  A: 0,
		  R: 0,
		  S: 0,
		  B: 0,
		  TO: 0
	  })
	  teamNameTwo = ""
	  teamIdTwo = ""
  }


</script>

<!--

<form on:submit|preventDefault={addTeam}>
  <input bind:value={teamId} placeholder="add Id">
  <input bind:value={teamName} placeholder="add Team">
  <button type="submit">Add</button>
</form>

<form on:submit|preventDefault={addTeamTwo}>
  <input bind:value={teamIdTwo} placeholder="add Id">
  <input bind:value={teamNameTwo} placeholder="add Team">
  <button type="submit">Add</button>
</form>

-->

<table>

  <thead>
    <tr>
	<div class="poo">
	  <th class="name"><span>E</span>ast teams</th>
	</div>
      <th>W</th>    <!--win-->
	  <th>L</th>    <!--lose-->
	  <th>A</th>    <!--assists-->
	  <th>R</th>    <!--rebounds-->
	  <th>S</th>    <!--steals-->
	  <th>B</th>    <!--blocks-->
	  <th>TO</th>   <!--turnovers-->
	</tr>
  </thead>

  <tbody>
  {#each EastTeams as team}
    <tr>
      <td class="name">{team.data().teamName}</td>
	  <td>{team.data().W}</td>
	  <td>{team.data().L}</td>
	  <td>{team.data().A}</td>
	  <td>{team.data().R}</td>
	  <td>{team.data().S}</td>
	  <td>{team.data().B}</td>
	  <td>{team.data().TO}</td>
	</tr>
  {/each}
  </tbody>

</table>


<table>

  <thead>
    <tr>
	<div class="poo">
	  <th class="name"><span>W</span>est teams</th>
	</div>
      <th>W</th>
	  <th>L</th>
	  <th>A</th>
	  <th>R</th>
	  <th>S</th>
	  <th>B</th>
	  <th>TO</th>
	</tr>
  </thead>

  <tbody>
  {#each WestTeams as team}
    <tr>
      <td class="name">{team.data().teamName}</td>
	  <td>{team.data().W}</td>
	  <td>{team.data().L}</td>
	  <td>{team.data().A}</td>
	  <td>{team.data().R}</td>
	  <td>{team.data().S}</td>
	  <td>{team.data().B}</td>
	  <td>{team.data().TO}</td>
	</tr>
  {/each}
  </tbody>

</table>

<div id="left"></div>
<div id="right"></div>




<style>

  * {
      font-family: 'Oranienbaum, Poppins, Roboto';
  }  

  form{
	  display: flex;
	  justify-content: center;
	  align-items: center;
  }

  #left{
	  width: 150px;
	  height: 100%;
	  position: fixed;
      z-index: 1;
      top: 0;
      left: 0;
	  background-image: url("https://s.yimg.com/ny/api/res/1.2/m98SlY0fYX29C.JEPpEezw--~A/YXBwaWQ9aGlnaGxhbmRlcjtzbT0xO3c9ODAw/http://media.zenfs.com/en/homerun/feed_manager_auto_publish_494/2894684b2e35579181886849e2de7a91");
	  box-shadow:  0px 0px 1px 3px rgba(97, 95, 95, 0.4);
	  background-position: center;
	  background-size: cover;
	  background-position: center;
	  
  }

  #right{
	  width: 150px;
	  height: 100%;
	  position: fixed;
      z-index: 1;
      top: 0;
      right: 0;
	  background-image: url("https://cdn.newsapi.com.au/image/v1/1f4e4ec0ce697db7ebc2bc88179c5443?width=1024");
	  box-shadow:  0px 0px 1px 3px rgba(97, 95, 95, 0.4);
      background-position: center;
	  background-size: cover;
	  background-position: center;

  }

table{
    width: 60%;
	border-collapse: collapse;
	margin: 100px auto 100px auto;
}

th, td{
    text-align: left;
    padding: 0.5rem 1rem;
}

thead tr{
	background-color: rgba(2, 47, 78, 0.7);
	box-shadow: 2px 3px 1px 0px rgba(15, 15, 15, 0.4);
	color: white;
}

.name{
	text-align: left;
}

tbody tr:nth-child(even){
	background-color: rgb(243, 228, 97);
	box-shadow: 2px 3px 1px 0px rgba(15, 15, 15, 0.4);
}

.poo{
    font-size: 20px;
}

span{
	color: rgb(209, 209, 209);
	font-size: 28px;
}

</style>