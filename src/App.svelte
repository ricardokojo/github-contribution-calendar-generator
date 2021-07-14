<script lang="ts">
  import TheHeader from "./lib/TheHeader.svelte";
  import TheFooter from "./lib/TheFooter.svelte";
</script>

<TheHeader />
<main>
  TODO
</main>
<TheFooter />

<style>
  @import url('https://fonts.googleapis.com/css2?family=Lato:wght@400;700;900&display=swap');

  :root {
    font-family: 'Lato', sans-serif;
  }

  :global(html) {
    @apply h-full;
  }

  :global(body) {
    @apply bg-gray-50 h-full;
  }

  :global(#app) {
    @apply flex flex-col items-center h-full;
  }
</style>
