<script>
	import {onMount} from 'svelte'
	const apiUrl = import.meta.env.VITE_API_URL
    let post;
    onMount(async () => {
    const res = await fetch(`${apiUrl}/wp/v2/pages?slug=employers`)
    const posts = await res.json()
    post= posts[0]
})
</script>

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
    {#if post}
        <p class="section-body">{@html post.content.rendered}</p> 
    {/if}
    <div class="button-wrapper">
      <a class='button' rel="external" href="https://www.edpa.org">LEARN MORE AT EDPA.ORG</a>
    </div>
    <div class="horizontal-line bottom"></div>
</div>

<style lang="scss">
  .section-container-employers {
	  margin-top: 50px;
    position: relative;
	  display: flex;
	  flex-direction: column;
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

  .section-body {
    font-family: 'Gilmer-Light';
    font-size: 18px;
    line-height: 1.5rem;
    margin-left: 36px;
    width: 80%;
	}
    
  .button-wrapper {
	  display: flex;
	  justify-content: center;
	  margin-bottom: 40px;
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
    &.bottom {
      height: 8px;
      margin-left: 0;
    }
	}
 
</style>