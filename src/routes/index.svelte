<script context="module">
	import Apply from '$lib/Apply.svelte'
	import WhyAlabama from '$lib/WhyAlabama.svelte'
	import About from '$lib/About.svelte'
</script>

<svelte:head>
	<title>Edpa Fuel</title>
</svelte:head>

<style>
	#skyline {
		width: 100%;
	}
	#internships {
		height: 500px;
	}
	img {
		width: 100%;
		object-fit: contain;
	}
</style>

<div id='skyline'><img alt='alabama' src="/city.jpeg"/></div>
<WhyAlabama/>
<div id='internships'>INTERNSHIPS</div>
<Apply/>
<About/>



