<script>
  import ExtensionalLogo from "../assets/logo.svg";

  let options = ["New", "Showcase", "Readme"];

  export let currentRoute = "valueInChild";
</script>

<main>
  <div
    class="bg-zinc-100 fixed top-0 flex border-b left-0 border-zinc-200 h-12 w-full"
  >
    <div class="flex-none h-12 w-14">
      <img class="mt-3 mx-auto h-6" alt="logo" src={ExtensionalLogo} />
    </div>

    <div class="flex-grow relative">
      {#each options as option}
        <button
          class="border-none outline-0 inline-block px-4 leading-10 mt-1 hover:opacity-100
            {currentRoute === option
            ? 'font-bold text-green-800'
            : 'opacity-50'}"
          on:click={() => (currentRoute = option)}
        >
          {option}
        </button>
      {/each}
    </div>

    <div class="flex-none w-12" />
  </div>
</main>

<style>
</style>
