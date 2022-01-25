<script>
	import {onMount} from 'svelte'
	let posts = []
	onMount(async () => {
		const res = await fetch('http://edpafuel.local/wp-json/wp/v2/posts')
		posts = await res.json()
		console.log(posts)
	})
</script>
<h1>Internships</h1>
<ul>
{#each posts as post}
	<li>{post.title.rendered}</li>
{/each}
</ul>
