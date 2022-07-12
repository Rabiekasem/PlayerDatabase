<style>
    *{
		font-family: 'Oranienbaum, Poppins, Roboto';
	}

	h1, figure, p {
		text-align: center;
		margin: 0 auto;
	}

	h1 {
		font-family: 'Oranienbaum, Poppins, Roboto';
		font-size: 1.8em;
		font-weight: 400;
		margin: 0.4em 0 0 0;
	}

	figure {
		margin: 0 0 1em 0;
	}

	img {
		width: 75%;
		height: 80vh;
		max-width: 400px;
		margin: 0 0 0.7em 0;
	}

	p {
		margin: 1em auto;
	}

	@media (min-width: 480px) {
		h1 {
			font-size: 4em;
		}
	}

	img{
		animation: scale 3s linear 1 ;
	}

	@keyframes scale {
		from{
			transform: scale(0.4);
		}
  to {
	transform: scale(1);
  }
}

h1{
	animation: change 3s linear 1;
}

@keyframes change {
	0%{
		letter-spacing: 5px;
	};
	
    50% {
        letter-spacing: 20px;
	};
	
    90%{
        letter-spacing: 5px;
        
    };
}


</style>

<svelte:head>
	<title>Nba season leaders</title>
</svelte:head>


<script>

  import {onMount} from "svelte" 

  let db
  let meldinger

</script>


<h1>Nba Players stats</h1>

<figure>
	<img alt='Nba' src='nba-logo.png'>
	<figcaption>National Basketball Association</figcaption>
</figure>

<p><strong>Season Leaders</strong></p>