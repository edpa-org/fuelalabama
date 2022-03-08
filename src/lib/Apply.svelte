<script>
	import {onMount} from 'svelte'
	const apiUrl = import.meta.env.VITE_API_URL
  let post;
  onMount(async () => {
  const res = await fetch(`${apiUrl}/wp/v2/pages?slug=apply`)
  const posts = await res.json()
  post= posts[0]
  //gets the featured image
  const imageUrl = post._links["wp:featuredmedia"][0].href;
  const imgRes = await fetch(`${imageUrl}`)
  const image = await imgRes.json()
  post.image = image.source_url
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
    <div class="image-wrapper">
      <img alt="apply" src={post.image}/>
    </div>
  </div>
{/if}
  
<style lang="scss">
  .section-container {
    max-width:1280px;
    margin: 0 32px 0 0;
    background-color: #26408f;
    min-height: 400px;
    position: relative;
    @media (max-width: 820px) {
      margin-right:0;
    }
  }
  .section-title-wrapper {
    position: relative;
    height: 118px;
    top: 50px;
    background-color:white;
    float: right;
    padding: 12px 0 0 16px;
    @media (max-width: 820px) {
      padding-right:12px;
    }
  }
  .section-title {
    font-family: 'Gilmer-Bold';
    font-size: 6vw;
    line-height: 6vw;
    color:white;
    -webkit-text-stroke: 2px #26408f;
    @media (max-width: 820px) {
      -webkit-text-stroke: 1px #26408f;
    }
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
     @media (max-width: 820px) {
      width: 60%;
    }
	}
  .image-wrapper {
    position: relative;
    right:0;
    top:0;
    height: 500px;
    margin-top: 50px;
    margin-left: 6%;
    @media (max-width: 820px) {
      height: unset;
      margin-top: 20px;
      width: 100%;
    }
  }
  img {
    max-width: 100%;
    max-height: 100%;
    display: block;
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