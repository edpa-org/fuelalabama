<script>
	const menu = ['home','internships','apply','about']
	const handleClick = (id) => document?.getElementById(id)?.scrollIntoView(true)
</script>

<style>
	nav {
		font-weight: 300;
		background-color: #1E1C5E;
		width: 100%;
		height: 118px;
		display: flex;
		align-items: center;
	}

	.title {
		display: flex;
		flex-basis: 70%;
		margin-left: 50px;
	}

	.title > img{
		max-width: 200px;
	}

	ul.menu {
		display: flex;
		flex-basis: 30%;
		padding-right: 20px;
	}

	li.menu {
		display: block;
		font-family: 'Gilmer-Light';
		padding: 1em 1em;
		text-transform: uppercase;
		color: white;
		cursor: pointer;
	}


</style>

<nav>
	<div class="title"><img alt='logo' src='/logo.png'/></div>
	<ul class='menu'>
		{#each menu as item}
			<li class='menu' on:click={()=>handleClick(item)}>
				{item}
			</li>
		{/each}
	</ul>
</nav>
