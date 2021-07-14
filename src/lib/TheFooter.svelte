<script>
  import GithubIcon from "../assets/svg/Github.svelte";
  import SvelteIcon from "../assets/svg/Svelte.svelte";
  import TailwindIcon from "../assets/svg/Tailwind.svelte";
  import TypescriptIcon from "../assets/svg/Typescript.svelte";
  import ViteIcon from "../assets/svg/Vite.svelte";
</script>

<footer>
  <p>made with Svelte <SvelteIcon /> + Typescript <TypescriptIcon /> + TailwindCSS <TailwindIcon /> + Vite <ViteIcon /> + Tea 🍵</p>
  <p>© MIT Licensed. Check this repository on <a href="#">GitHub <GithubIcon /></a></p>
</footer>

<style>
  footer {
    @apply border-t border-gray-200 fixed bottom-0 pt-2 pb-6;
  }
  
  footer > p {
    @apply text-sm text-gray-500 mt-1 flex justify-center;
  }
  
  footer > p > a {
    @apply ml-1 flex underline;
  }
</style>
