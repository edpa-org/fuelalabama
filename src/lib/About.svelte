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
      title:"About",
      body: "The goal for EDPA’s talent website is, first and foremost, to showcase internships and entry-level opportunities to young professional talent in Alabama and to generate applications for the EDPA’s first-ever Fuel Alabama Fellowship, a supplemental internship program for the state’s best and brightest interns at compelling companies.",
      image:"/about.png"
    }
</script>
<div id="about" class="section-container">
  <div class="section-title-wrapper">
    <div class="section-title">
      {section.title}
    </div>
    <p class="section-body">{section.body}</p>
  </div>
   <div class="image-wrapper">
    <img alt="about" src={section.image}/>
  </div>
</div>
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
  .section-title-wrapper {
    position: relative;
    display: flex;
    flex-flow: column;
    width: 40%;
    top: 50px;
    background-color:white;
    padding: 12px 0 0 16px;
    margin-left: 30%;
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