<script>
  import New from "./lib/New/index.svelte";
  import Showcase from "./lib/Showcase.svelte";
  import Readme from "./lib/Readme.svelte";
  import Navigation from "./lib/Navigation.svelte";

  let currentRoute = "New";
</script>

<main class="h-screen text-left pt-12">
  <Navigation bind:currentRoute />

  {#if currentRoute === "New"}
    <New />
  {/if}

  {#if currentRoute === "Showcase"}
    <Showcase />
  {/if}

  {#if currentRoute === "Readme"}
    <Readme />
  {/if}
</main>

<style>
  @tailwind base;
  @tailwind components;
  @tailwind utilities;
</style>
