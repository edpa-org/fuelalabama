<script context="module">
	import Apply from '$lib/Apply.svelte'
	import WhyAlabama from '$lib/WhyAlabama.svelte'
	import About from '$lib/About.svelte'
	import Internships from '$lib/Internships.svelte'
	import Footer from '$lib/Footer.svelte'
	import Work from '$lib/Work.svelte'
	import Play from '$lib/Play.svelte'
	import Live from '$lib/Live.svelte'
	import GreenTitle from '$lib/GreenTitle.svelte'

</script>

<svelte:head>
	<title>Edpa Fuel</title>
</svelte:head>

<style>
	#skyline {
		display: flex;
		background-color: #1E1C5E;
	}
	img {
		width: 90%;
		object-fit: contain;
	}

</style>

<div id='skyline'><img alt='alabama' src="/city.jpeg"/></div>
//Todo :Create templates instead of creating similar components and have dynamic url fetches, render pages with order 
<GreenTitle/>
<div id="home">
  <Work/>
  <Live/>
  <Play/>  
</div>
<Internships/>
<Apply/>
<About/>
<Footer/>



