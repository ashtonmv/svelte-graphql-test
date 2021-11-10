<script context="module">
  import { GraphQLClient } from 'graphql-request';
  export async function load() {
    const graphcms = new GraphQLClient(
      'https://api-eu-central-1.graphcms.com/v2/ckvtmnbn9001p01xsgk0j7j8h/master',
      {
        headers: {},
      }
    )
    const { posts } = await graphcms.request(
      `query Posts { 
        posts {
          title
          content
        }
      }`
    )
    return {
      props: {
        posts,
      },
    }
  }
</script>

<script>
  export let posts
</script>

<svelte:head>
  <title>SvelteKit project template</title>
</svelte:head>

<h1>GraphCMS with SvelteKit and GraphQL Request</h1>

{#each posts as post}
  <p>{post.title}</p>
  <p>{post.content}</p>
{/each}
