<script>
  const section =
    {
      title:"Internships",
      image:"/internships.png"
    }
</script>
<div>
	<div id="interships" class="section-container">
		<img alt="internships" src={section.image}/>
		<div>
			<div class="section-title">
			{section.title}
			</div>
		</div>
	 </div>
	 <div class="section-container-employer">
		<div class="section-small-title">
			Employers
		</div>
		 <div class="section-title">
			 Host a Fellow
		 </div>
		 <div class="button-wrapper">
			<a class='button' rel="external" href="https://www.edpa.org">LEARN MORE AT EDPA.ORG</a>
		 </div>
	 </div>
</div>

<style lang="scss">
  .section-container {
	margin-top: 50px;
    position: relative;
	display: flex;
  }
  .section-container-employer {
	margin-top: 50px;
    position: relative;
	display: flex;
	flex-direction: column;
	height: 300px;
	margin-left: 50px;
  }
  .section-title {
    font-family: 'Gilmer-Bold';
    font-size: 92px;
    line-height: 92px;
    color:white;
    -webkit-text-stroke: 1px #05e37a;
  }
  .section-small-title {
    font-family: 'Gilmer-Heavy';
    font-size: 50px;
    color:#05e37a;
  }

  .button-wrapper {
	  display: flex;
	  justify-content: center;
	  margin-top: 50px;
  }
  a.button {
	display:inline-block;
	padding:0.46em 1.6em;
	border:0.1em solid #000000;
	border-radius: 5rem;
	text-decoration:none;
	font-family:'Roboto',sans-serif;
	color:#000000;
	text-align:center;
  }

 
@font-face {
 font-family: 'Gilmer-Heavy';
  src: url('../public/fonts/Gilmer-Heavy.otf');
}
@font-face {
  font-family: 'Gilmer-Bold';
  src: url('../public/fonts/Gilmer-Bold.otf');
}
</style>