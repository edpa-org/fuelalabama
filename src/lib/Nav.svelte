<script>
    import {onMount} from 'svelte'
    const apiUrl = import.meta.env.VITE_API_URL
    let pages = [];
    onMount(async () => {
		const res = await fetch(`${apiUrl}/wp/v2/pages?per_page=20`)
		pages = await res.json()
		pages = pages.filter(p => p.is_nav_menu === "true")
		pages.sort((a,b) => (a.menu_order > b.menu_order) ? 1 : -1)
    })
	const handleClick = (id) => document?.getElementById(id)?.scrollIntoView(true)
</script>

<style lang='scss'>
	nav {
		font-weight: 300;
		background-color: #1E1C5E;
		width: 100%;
		height: 118px;
		display: flex;
		align-items: center;
		@media screen and (max-width: 425px) {
			flex-direction: column;
		}
	}

	.logo {
		display: flex;
		flex-basis: 70%;
		margin-left: 50px;
	}

	img {
		width: 100%;
		height: auto;
		max-width: 200px;
		@media screen and (max-width: 425px) {
			max-width: 100px;
		}
		@media screen and (min-width: 425px) {
			min-width: 100px;
		}
	}

	ul.menu {
		display: flex;
		flex-basis: 30%;
		padding-right: 20px;
		@media screen and (min-width: 425px) {
			padding-left: 0px;
		}
	}

	li.menu {
		display: block;
		font-family: 'Gilmer-Light';
		padding: 1em 1em;
		text-transform: uppercase;
		color: white;
		cursor: pointer;
		@media screen and (max-width: 768px) {
			font-size: 12px;
		}
	}


</style>

<nav>
	<div class="logo"><img alt='logo' src='/logo.png'/></div>
	<ul class='menu'>
		{#each pages as p}
			<li class='menu' on:click={()=>handleClick(p.id)}>
				{p.title.rendered}
			</li>
		{/each}
	</ul>
</nav>
