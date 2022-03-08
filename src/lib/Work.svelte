<script>
import {onMount} from 'svelte'
	const apiUrl = import.meta.env.VITE_API_URL
  let page;
  let growingIndustryPage;
  onMount(async () => {
  const res = await fetch(`${apiUrl}/wp/v2/pages?slug=work`)
  const pages = await res.json()
  page= pages[0]
  //gets the featured image
  const imageUrl = page._links["wp:featuredmedia"][0].href;
  const imgRes = await fetch(`${imageUrl}`)
  const image = await imgRes.json()
  page.image = image.source_url

  const growingIndustryResponse = await fetch(`${apiUrl}/wp/v2/pages?slug=growing-industry`).then(res => res.json())
  growingIndustryPage = growingIndustryResponse[0]
})
</script>
{#if page}
  <div id={page.id} class="section-container">
    <div class="image-wrapper">
    <img alt="about" src={page.image}/>
    </div>
    <div class="section-title-wrapper">
      <div class="section-title">
        {page.title.rendered}
      </div>
      <p class="section-body">{@html page.content.rendered}</p>
      {#if growingIndustryPage}
        <div class="section-title">
          {growingIndustryPage.title.rendered}
        </div>
        <p class="section-body">{@html growingIndustryPage.content.rendered}</p>
      {/if}
    </div>
  </div>
{/if}
<style lang="scss">
  .section-container {
    display: flex;
    flex-flow: row;
    margin: 0 50px 32px 32px;
    position: relative;
    width: 90%;
    align-items: flex-start;
    @media (max-width: 820px) {
      flex-flow: column;
      align-items: flex-end;
      margin: 0;
      padding: 16px 0;
      width: 100%;
    }
  }
  .image-wrapper {
    position: relative;
    right:0;
    top:0;
    height: 450px;
    margin-top: 100px;
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
  .section-title-wrapper {
    position: relative;
    display: flex;
    flex-flow: column;
    width: 40%;
    padding: 12px 0 0 16px;
    margin-left: 8%;
    @media (max-width: 820px) {
      width: 95%;
    }
  }
  .section-title {
    font-family: 'Gilmer-Bold';
    font-size: 6vw;
    line-height: 6vw;
    color:white;
    -webkit-text-stroke: 2px #05e37a;
    @media (max-width: 820px) {
      -webkit-text-stroke: 1px #05e37a;
      font-size: 40px;
      margin-top: 8px;
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
    text-align: left;
    width: 90%;
    @media (max-width: 820px) {
      margin-bottom: 16px;
    }
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