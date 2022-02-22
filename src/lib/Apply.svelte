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

@font-face {
 font-family: 'Gilmer-Light';
  src: url('../public/fonts/Gilmer-Light.otf');
}
@font-face {
  font-family: 'Gilmer-Bold';
  src: url('../public/fonts/Gilmer-Bold.otf');
}
</style>