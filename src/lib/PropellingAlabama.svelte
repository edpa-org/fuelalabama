<script>
  import {onMount} from 'svelte'
  const apiUrl = import.meta.env.VITE_API_URL
  let page;
  onMount(async () => {
    const res = await fetch(`${apiUrl}/wp/v2/pages?slug=propelling-alabama`)
    const pages = await res.json()
    page= pages[0]
  })
</script>

{#if page}
  <h1 id="home" class="sections-title">{page.title.rendered}</h1>
{/if}

<style lang="scss">
  .sections-title {
    font-family: 'Gilmer-Light';
    font-size: 68px;
    text-align: left;
    text-transform:uppercase;
    color: white;
    background-color: #05e37a;
    padding: 24px;
    margin: 0;
    max-width: 800px;
  }
</style>
