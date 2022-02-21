<script>
	import {onMount} from 'svelte'
	const apiUrl = import.meta.env.VITE_API_URL
  let post;
  onMount(async () => {
  const res = await fetch(`${apiUrl}/wp/v2/pages?slug=apply`)
  const posts = await res.json()
  post= posts[0]
})
</script>
{#if post}
  <div id={post.id} class="section-container">
    <div class="section-title-wrapper">
      <div class="section-title">
        {post.title.rendered}
      </div>
    </div>
    <p class="section-body">{@html post.content.rendered}</p>
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
  
<style lang="scss">
  .section-container {
    max-width:1280px;
    margin: 0 32px 0 0;
    background-color: #26408f;
    min-height: 400px;
    position: relative;
  }
  .section-title-wrapper {
    position: relative;
    height: 118px;
    top: 50px;
    background-color:white;
    float: right;
    padding: 12px 0 0 16px;
  }
  .section-title {
    font-family: 'Gilmer-Bold';
    font-size: 92px;
    line-height: 92px;
    color:white;
    -webkit-text-stroke: 1px #26408f;
  }
	.section-body {
    position: relative;
    font-family: 'Gilmer-Light';
    font-size: 18px;
    background-color:white;
    line-height: 1.5rem;
    width: 50%;
    padding: 16px;
    margin-bottom: 0;
    margin-left: 6%;
    text-align: left;
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
 font-family: 'Gilmer-Light';
  src: url('../public/fonts/Gilmer-Light.otf');
}
@font-face {
  font-family: 'Gilmer-Bold';
  src: url('../public/fonts/Gilmer-Bold.otf');
}
</style>