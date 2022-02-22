<script context="module">
	import Apply from '$lib/Apply.svelte'
	import About from '$lib/About.svelte'
	import Internships from '$lib/Internships.svelte'
	import Footer from '$lib/Footer.svelte'
	import WhyAlabama from '$lib/WhyAlabama.svelte'
	import Play from '$lib/Play.svelte'
	import Work from '$lib/Work.svelte'
  import Employers from '$lib/Employers.svelte';
  import PropellingAlabama from '$lib/PropellingAlabama.svelte';
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
  .green-rectangle {
    position: relative;
    width: 70%;
    left:30%;
    height: 30px;
    background-color: #05e37a;
  }

</style>

<div id='skyline'>
    <img alt='alabama' src={heroPage.image}/>
</div>
<PropellingAlabama/>
<div id="home">
  <WhyAlabama/>
  <Work/>
  <Play/>  
  <div class="green-rectangle"></div>
</div>
<Internships/>
<Apply/>
<Employers/>
<About/>
<Footer/>



