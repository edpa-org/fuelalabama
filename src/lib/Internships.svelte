<script>
	import {onMount} from 'svelte'
	const apiUrl = import.meta.env.VITE_API_URL
  let post;
  const section =
    {
      title:"Internships",
      image:"/internships.png"
    }
  onMount(async () => {
  const res = await fetch(`${apiUrl}/wp/v2/pages?slug=internships`)
  const posts = await res.json()
  post= posts[0]
})
</script>

<div>
	<div id="interships" class="section-container">
		<img alt="internships" src={section.image}/>
		<div>
			<div class="section-title">
			{section.title}
			</div>
			{#if post}
				<div id="internships" class="section-container">
					<div class="section-title-wrapper">
						<div class="section-title">
							{post.title.rendered}
						</div>
					</div>
					<p class="section-body">{@html post.content.rendered}</p>
				</div>
			{/if}
		</div>
	 </div>
	 <div class="section-container-employer">
		<div class="section-small-title">
			Employers
		</div>
		 <div class="section-title">
			 Host a Fellow
		 </div>
		 <div class="button-wrapper">
			<a class='button' rel="external" href="https://www.edpa.org">LEARN MORE AT EDPA.ORG</a>
		 </div>
	 </div>
</div>

<style lang="scss">
  .section-container {
	margin-top: 50px;
    position: relative;
	display: flex;
  }
  .section-container-employer {
	margin-top: 50px;
    position: relative;
	display: flex;
	flex-direction: column;
	height: 300px;
	margin-left: 50px;
  }

  .section-small-title {
    font-family: 'Gilmer-Heavy';
    font-size: 50px;
    color:#05e37a;
  }

  .button-wrapper {
	  display: flex;
	  justify-content: center;
	  margin-top: 50px;
  }
  a.button {
	display:inline-block;
	padding:0.46em 1.6em;
	border:0.1em solid #000000;
	border-radius: 5rem;
	text-decoration:none;
	font-family:'Roboto',sans-serif;
	color:#000000;
	text-align:center;
  }

  .section-body {
    position: relative;
    font-family: 'Gilmer-Light';
    font-size: 18px;
    background-color:white;
    line-height: 1.5rem;
    padding: 16px;
    margin-bottom: 0;
    margin-top: 0;
    margin-left: 6%;
    bottom: 0;
    text-align: left;
	}

 
@font-face {
 font-family: 'Gilmer-Heavy';
  src: url('../public/fonts/Gilmer-Heavy.otf');
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