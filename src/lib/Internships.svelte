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
	 <div class="section-container-employers">
		  <div class="horizontal-line"></div>
		<div class="section-title-employers-small">
			Employers
		</div>
		<div class="section-title-wrapper-employers">
			<div class="vertical-line">
			</div>
			<div class="section-title-employers">
				Host a Fellow
			</div>
		</div>
		<div class="button-wrapper">
			<a class='button' rel="external" href="https://www.edpa.org">LEARN MORE AT EDPA.ORG</a>
		</div>
	 </div>
</div>

<style lang="scss">
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

	ul.wp-block-rss {
		padding: 0;
	}
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

  .section-container-employers {
	margin-top: 50px;
    position: relative;
	display: flex;
	flex-direction: column;
	height: 300px;
	margin-left: 50px;
  }

  .section-title-wrapper-employers {
		display: flex;
	}

  .section-title-employers {
    font-family: 'Gilmer-Bold';
    font-size: 92px;
    line-height: 92px;
    color:white;
	margin-left: 30px;
    -webkit-text-stroke: 2px #1E1C5E;
  }
  
  .section-title-employers-small {
    font-family: 'Gilmer-Heavy';
    font-size: 50px;
    color:#1E1C5E;
  }

  .button-wrapper {
	  display: flex;
	  justify-content: center;
	  margin-top: 30px;
  }
  a.button {
	display:inline-block;
	padding:0.46em 1.6em;
	border:0.1em solid #000000;
	border-radius: 5rem;
	text-decoration:none;
	font-family:'Gilmer-Light';
	color:white;
	text-align:center;
	background-color: #1E1C5E;
  }

	.vertical-line {
		display: block;
		border-left: 6px solid #1E1C5E;
		height: 100px;
	}

	.horizontal-line {
	position: relative;
	margin-left: 36px;
	height: 30px;
	background-color: #1E1C5E;
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