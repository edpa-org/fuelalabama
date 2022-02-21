<script context="module">
	import Apply from '$lib/Apply.svelte'
	import About from '$lib/About.svelte'
	import Internships from '$lib/Internships.svelte'
	import Footer from '$lib/Footer.svelte'
	import Work from '$lib/Work.svelte'
	import Play from '$lib/Play.svelte'
	import Live from '$lib/Live.svelte'
	import GreenTitle from '$lib/GreenTitle.svelte'
</script>

<script>
    import {onMount} from 'svelte'
    const apiUrl = import.meta.env.VITE_API_URL
    let heroPage = {};
    onMount(async () => {
        const res = await fetch(`${apiUrl}/wp/v2/pages?slug=hero-image`)
        heroPage = await res.json()
        heroPage = heroPage[0]
        //gets the featured image
        const imageApi = heroPage._links["wp:featuredmedia"][0].href;
        const imgRes = await fetch(imageApi)
        const image = await imgRes.json()
        heroPage.image = image.source_url
    })
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
		width: 100%;
		object-fit: contain;
	}

</style>

<div id='skyline'>
    <img alt='alabama' src={heroPage.image}/>
</div>
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



