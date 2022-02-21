<script>
	import {onMount} from 'svelte'
	const apiUrl = import.meta.env.VITE_API_URL
  let page;

  onMount(async () => {
	const res = await fetch(`${apiUrl}/wp/v2/pages?slug=internships`)
	const pages = await res.json()
	page= pages[0]

	const imageUrl = page._links["wp:featuredmedia"][0].href;
	const imgRes = await fetch(`${imageUrl}`)
	const image = await imgRes.json()
	page.image = image.source_url
})
</script>

<div>
  	{#if page}
		<div id={page.id} class="section-container-internships">
					<div class="section-container-image">
						<img alt="internships" src={page.image}/>
					</div>
					<div>
						<div class="section-title-wrapper-internships">
							<div class="section-title-internships">
								{page.title.rendered}
							</div>
						</div>
						<div class="section-body-wrapper">
							<p class="section-body-internships">{@html page.content.rendered}</p>
						</div>
					</div>
		</div>
	  {/if}
</div>

<style lang="css">
  .section-container-internships {
    position: relative;
	  display: flex;
  	margin-right: 20px;
  }

  .section-container-image {
	  margin-right: 40px;
  }

  .section-title-wrapper-internships {
    display: flex;
    justify-content: flex-end;
    background-color: white;
  }

  .section-title-internships {
    font-family: 'Gilmer-Bold';
    font-size: 92px;
    line-height: 92px;
    color:white;
    -webkit-text-stroke: 2px #05e37a;
    margin-bottom: 20px;
  }

  .section-body-wrapper {
	  height: 400px;
	  overflow: scroll;
	  margin-top: 5px;
  }

  .section-body-internships {
    position: relative;
    font-family: 'Gilmer-Light';
    font-size: 18px;
    background-color:white;
	text-decoration: none;
    margin-left: 40px;

  }
  	p :global(ul) {
		list-style: none;
		padding: 0;
	}
	p :global(li) {
		list-style: none;
		margin-bottom: 20px;
		font-family: 'Gilmer';
		font-size: 12px;
	}

	:global(a) {
		font-size: 16px;
		font-family: 'Gilmer-Bold';
		color: #1E1C5E;
		cursor: pointer;
		text-decoration: none;
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