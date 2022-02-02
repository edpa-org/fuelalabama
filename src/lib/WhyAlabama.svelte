<script>
	import {onMount} from 'svelte'
	let posts = []
	const apiUrl = import.meta.env.VITE_API_URL
	onMount(async () => {
		const res = await fetch(`${apiUrl}/wp/v2/posts`)
		posts = await res.json()
	})
  const sections = [
    {
      title:"Work",
      body: "From 30 Fortune 1000s, of which 16 are Fortune 500s, to more than 700 startups, Alabama has transformed into a top tech market where inventive minds can make their mark.",
      image: "/work.jpg"
    },
    {
      title:"Live",
      body: "Your hard work goes a long way in ALA, one of the most affordable major metros in the nation.",
      image: "/live.jpg"
    },
    {
      title:"Play",
      body: "In 1864, Alabama burned to ashes and rose again. 100 years later, Civil Rights leaders stood up to demand equality for all.The beauty that comes from these battle wounds still runs through the veins of Alabama's culture — instilling purpose into the music, food, fashion and art. Living in ALA puts you at the root of it all.",
      image: "/play.jpg"
    },
  ]
</script>
<h1 id="home" class="sections-title">Alabama for all</h1>
<div class="sections-container">
  {#each sections as section}
  <div class="section-wrapper">
    <div class="section">
      <div class=section-title>
        {section.title}
      </div>
      <p class="section-body">{section.body}</p>
    </div>
    <div class="section-image">
      <img alt='alabama' src={section.image}/>
    </div>
  </div>
  {/each}
</div>
<div class="rectangle"></div>
<style lang="scss">
  .sections-title {
    font-family: 'Gilmer-Light';
    font-size: 84px;
    text-align: left;
    text-transform:uppercase;
    color: white;
    /* background-color: #26408f; */
    background-color: #05e37a;
    padding: 24px;
    margin: 0;
    max-width: 800px;
  }
  .sections-container {
    max-width:1280px;
    display: flex;
    flex-flow: column wrap;
    align-content: flex-start;
    align-items: flex-start;
    margin: 0 32px 32px;
  }
  .sections-container > :global(:nth-child(odd)){
    display: flex;
    flex-flow: row;
  }
  .sections-container > :global(:nth-child(even)){
    display: flex;
    flex-flow: row-reverse;
    justify-content: flex-end;
  }
  .section-wrapper {
    position: relative;
    margin: 0 32px 32px 32px;
    width: 100%;
    height: 450px;
    display: flex;
  }
  .section {
    display: flex;
    flex-flow: column;
    width: 40%;
    background-color: white;
    z-index: 2;
    margin-left: 10%;
    margin-top: 10%;
    box-sizing: content-box;
  }
  .section-image {
    height: 400px;
    width: 60%;
  }
  .section-title {
    font-family: 'Gilmer-Bold';
    font-size: 92px;
    line-height: 92px;
    color:white;
    -webkit-text-stroke: 1px #05e37a;
  }
	.section-body {
    font-family: 'Gilmer-Light';
    font-size: 18px;
    line-height: 1.5rem;
    width: 70%;
    align-self: flex-end;
    padding: 0 10px;
	}
  img {
		width: 100%;
    max-height: 100%;
    object-fit: contain;
	}
  .rectangle {
    position: relative;
    width: 70%;
    left:30%;
    height: 30px;
    background-color: #05e37a;
  }
@font-face {
 font-family: 'Gilmer-Light';
  src: url('../public/fonts/Gilmer-Light.otf');
}
@font-face {
  font-family: 'Gilmer-Bold';
  src: url('../public/fonts/Gilmer-Bold.otf');
}
</style>

<!-- <ul>
{#each posts as post}
	<li>
		<a rel='prefetch' href='articles/{post.slug}'>
			{post.title.rendered}
		</a>
  </li>
{/each}
</ul> -->