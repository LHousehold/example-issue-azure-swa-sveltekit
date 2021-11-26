<script context="module">
  export const ssr = false;
</script>

<script>
  import { onMount } from 'svelte';

  console.log('script');

  let x = "Default"; // runs server side

  onMount(async () => {
    console.log('mount');

    x = "Updated with Javascript"; // runs client side
  });
</script>

<h1 class="seethis">This should be light grey</h1>
{x}

<style>
  .seethis {
    color: #f1f1f1;
  }
</style>