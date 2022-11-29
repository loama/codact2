<script>
  let options = [
    {
      name: "Blinking",
      link: "",
    },
    {
      name: "Optical Illusion",
      link: "",
    },
    {
      name: "Writing Sort",
      link: "",
    },
    {
      name: "Press Space",
      link: "",
    },
    {
      name: "Fear the mouse",
      link: "",
    },
    {
      name: "Square in circle",
      link: "",
    },
    {
      name: "Moving dots",
      link: "",
    },
    {
      name: "Mandelbrot",
      link: "",
    },
    {
      name: "Spinning Boxes",
      link: "",
    },
  ];
</script>

<div class="mt-10 gap-4 grid grid-cols-3 h-20 mx-auto max-w-3xl">
  {#each options as option}
    <button class="mb-4 cursor-pointer hover:opacity-80">
      <div class="text-left">{option.name}</div>
      <div class="bg-zinc-400 h-32 rounded-md w-full" />
    </button>
  {/each}
</div>
