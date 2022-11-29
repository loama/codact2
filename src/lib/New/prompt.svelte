<script>
  let prompts = [];

  let currentQuestion = "";

  function handleOnSubmit() {
    if (currentQuestion.length === 0) {
      return;
    }

    console.log(currentQuestion);
    prompts.push({
      question: currentQuestion,
      answer:
        "Apologies, our servers are currently overloaded. Try again tomorrow!",
    });
    prompts = prompts;

    const chat = document.getElementById("chat");
    setTimeout(() => {
      chat.scrollTo({
        top: chat.scrollHeight,
        behavior: "smooth",
      });
    }, 100);
    currentQuestion = "";
  }
</script>

<div class="h-full">
  <div class="p-2 font-bold text-sm">PROMPT</div>
  <div id="chat" class="p-2 overflow-y-scroll w-full">
    {#each prompts as prompt}
      <div>> {prompt.question}</div>
      <div class="text-zinc-500 text-sm mb-4">{prompt.answer}</div>
    {/each}
  </div>

  <form class="relative" on:submit|preventDefault={handleOnSubmit}>
    <input
      class="border-t border-zinc-200 h-10 outline-none px-2 w-full"
      type="text"
      placeholder="type your prompt here..."
      bind:value={currentQuestion}
    />
    <input
      type="submit"
      class="absolute duration-300 h-8 mt-1 right-1 px-3 rounded-sm transition
        {currentQuestion.length > 0
        ? 'bg-green-600 text-white'
        : 'bg-zinc-200'}"
      value="Send"
    />
  </form>
</div>

<style>
  #chat {
    height: calc(100% - 36px - 40px);
  }
</style>
