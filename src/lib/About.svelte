<script>
import {onMount} from 'svelte'
	const apiUrl = import.meta.env.VITE_API_URL
  let post;
  onMount(async () => {
  const res = await fetch(`${apiUrl}/wp/v2/pages?slug=about`)
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
      <p class="section-body">{@html post.content.rendered}</p>
    </div>
    <div class="image-wrapper">
      <img alt="about" src={post.image}/>
    </div>
  </div>
{/if}
<style lang="scss">
  .section-container {
    margin: 0 0 32px 0;
    position: relative;
    @media screen and (max-width: 768px) {
      display: flex;
      flex-direction: column;
    }
  }
  .image-wrapper {
    @media screen and (min-width: 768px) {
      position: absolute;
      right:0;
      top:0;
    }
  }
  img {
    max-height: 500px;
    @media screen and (max-width: 768px) {
      width: 100%;
    }
  }
  .section-title-wrapper {
    position: relative;
    display: flex;
    flex-flow: column;
    background-color:white;
    padding: 12px 0 0 16px;
    z-index: 2;
    @media screen and (min-width: 768px) {
      margin-left: 10%;
      width: 50%;
    }
    @media screen and (min-width: 1024px) {
      margin-left: 20%;
      width: 40%;
    }
  }
  .section-title {
    font-family: 'Gilmer-Bold';
    font-size: 6vw;
    line-height: 6vw;
    color:white;
    -webkit-text-stroke: 2px #05e37a;
    margin-top:16px;
    @media screen and (max-width: 820px) {
      -webkit-text-stroke: 1px #05e37a;
      font-size: 40px;
      margin-bottom: 8px;
    }
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
 font-family: 'Gilmer-Light';
  src: url('../public/fonts/Gilmer-Light.otf');
}
@font-face {
  font-family: 'Gilmer-Bold';
  src: url('../public/fonts/Gilmer-Bold.otf');
}
</style>