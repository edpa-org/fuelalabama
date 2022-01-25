<script context="module">
  const apiUrl = import.meta.env.VITE_API_URL;
  export async function load({ params }) {
    const res = await fetch(`${apiUrl}/wp/v2/posts?slug=${params.slug}`);
    const data = await res.json();
    return {
        props: {
            post: data[0],
        },
    };
  }
</script>

<script>
  export let post;
</script>

<h1>{post.title.rendered}</h1>

<div class="content">
  {@html post.content.rendered}
</div>
