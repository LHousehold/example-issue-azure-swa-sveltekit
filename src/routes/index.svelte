<script>
  import { onMount } from 'svelte';

  console.log('script');

  let x = "Default"; // runs server side

  onMount(async () => {
    console.log('mount');

    x = "Updated with Javascript"; // runs client side
  });
</script>

<h1>Welcome to SvelteKit</h1>
<p>Visit <a href="https://kit.svelte.dev">kit.svelte.dev</a> to read the documentation</p>
{x}

<style>
  p {
    color: blue;
  }
</style>