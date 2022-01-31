<script>
	const menu = {
		'home': ['work','live','play'],
		'internships': ['internship opportunties','host a fellow'],
		'apply': ['requirements','application'],
		'about': ['edpa','retain alabama research','legal']
	}

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

	div.dropdown {
		display: none;
		align-items: center;
		width: 100%;
		height: auto;
		padding-bottom: 5px;
		background-color: #1E1C5E;
		position:fixed;
		top: 110px;
		left: 0;
		z-index: 10;
	}

	ul.menu {
		display: flex;
		flex-basis: 30%;
		padding-right: 20px;
	}

	ul.dropdown {
		display: flex;
		flex-direction: column;
		margin-left: 50px;
	}

	li.menu {
		display: block;
		font-family: 'Gilmer-Bold';
		padding: 1em 0.5em;
		text-transform: capitalize;
		color: white;
		cursor: pointer;
	}

	.line {
		display: block;
		border-left: 6px solid #ffff;
		height: 100px;
	}

	li.dropdown {
		display: block;
		padding: 5px 0;
		font-family: 'Gilmer-Light';
		text-transform: uppercase;
		color: #ffff;
		font-size: 30px;
	}

	li:hover > div {
		display: flex;
	}
</style>

<nav>
	<div class="title"><img alt='logo' src='/logo.png'/></div>
	<ul class='menu'>
		{#each Object.entries(menu) as [key, values]}
			<li class='menu' on:click={()=>handleClick(key)}>
				{key}
				<div class='dropdown'>
					<div class='line'></div>
					<ul class='dropdown'>
						{#each values as value }
							<li class='dropdown'>
								{value}
							</li>
						{/each}
					</ul>
				</div>
			</li>
		{/each}
	</ul>
</nav>
