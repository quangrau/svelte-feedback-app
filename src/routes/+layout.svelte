<script>
  import "../app.css";
</script>

<svelte:head>
  <title>SvelteKit Feedback Demo</title>
</svelte:head>

<main class="container mx-auto p-6 md:p-10 max-w-4xl">
  <slot />
</main>
<footer class="p-6 text-center text-xs font-light text-gray-500">
  Find me at <a class="text-gray-400 underline" target="_blank" rel="noreferrer" href="https://quangrau.com">quangrau.com</a>
</footer>