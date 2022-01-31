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
  <div id="about" class="section-container">
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
  }
  .image-wrapper {
    position: absolute;
    right:0;
    top:0;
  }
  img {
    max-height: 500px;
  }
  .section-title-wrapper {
    position: relative;
    display: flex;
    flex-flow: column;
    width: 40%;
    top: 50px;
    background-color:white;
    padding: 12px 0 0 16px;
    margin-left: 20%;
    z-index: 2;
  }
  .section-title {
    font-family: 'Gilmer-Bold';
    font-size: 92px;
    line-height: 92px;
    color:white;
    -webkit-text-stroke: 1px #05e37a;
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