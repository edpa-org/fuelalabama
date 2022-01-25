<script>
	// import {onMount} from 'svelte'
	// let posts = []
	// const apiUrl = import.meta.env.VITE_API_URL
	// onMount(async () => {
	// 	const res = await fetch(`${apiUrl}/wp/v2/posts`)
	// 	posts = await res.json()
	// })
  const section =
    {
      title:"Apply",
      body: "The goal for EDPA’s talent website is, first and foremost, to showcase internships and entry-level opportunities to young professional talent in Alabama and to generate applications for the EDPA’s first-ever Fuel Alabama Fellowship, a supplemental internship program for the state’s best and brightest interns at compelling companies.",
    }
</script>
<div id="apply" class="section-container">
  <div class="section-title-wrapper">
    <div class="section-title">
      {section.title}
    </div>
  </div>
  <p class="section-body">{section.body}</p>
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
    width: 300px;
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
    position: absolute;
    font-family: 'Gilmer-Light';
    font-size: 18px;
    background-color:white;
    line-height: 1.5rem;
    width: 50%;
    padding: 16px;
    margin-bottom: 0;
    margin-left: 6%;
    bottom: -1px;
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