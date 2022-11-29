<script>
  import axios from "axios";

  let prompts = [];

  let currentQuestion = "";

  async function handleOnSubmit() {
    if (currentQuestion.length === 0) {
      return;
    }

    console.log(currentQuestion);

    const params = new URLSearchParams();
    params.append("selectionStart", "0");
    params.append("selectionEnd", "0");
    params.append("title", "Applying color with JavaScript");
    params.append("useContext", "true");
    params.append("question", currentQuestion);

    try {
      const res = await axios.post(
        `https://codact.dev/?gen=clb1oa0by0018vy72th2fsvwi`,
        {
          headers: {},
          params: params,
        }
      );
      console.log(res);
    } catch (e) {
      console.log(e);
    }

    /* let functionText = `
      var c = document.getElementById('myCanvas');
      var ctx = c.getContext('2d');
      ctx.beginPath();
      ctx.arc(100, 75, 50, 0, Math.PI * 2, true);
      ctx.stroke();
      var c = document.getElementById('myCanvas');
      var ctx = c.getContext('2d');
      ctx.beginPath();
      ctx.arc(100, 75, 50, 0, Math.PI * 2, true);

      for (var i = 0; i < 10; i++) {
          ctx.strokeStyle = "rgb(" + (Math.floor(Math.random() * 256)) + "," + (Math.floor(Math.random() * 256)) + "," + (Math.floor(Math.random() * 256)) + ")";
          ctx.stroke();
      }
      var c = document.getElementById('myCanvas');
      var ctx = c.getContext('2d');
      ctx.beginPath();
      ctx.arc(100, 75, 50, 0, Math.PI * 2, true);

      var throb = setInterval(function() {
          ctx.clearRect(0, 0, c.width, c.height);

          ctx.strokeStyle = "rgb(" + (Math.floor(Math.random() * 256)) + "," + (Math.floor(Math.random() * 256)) + "," + (Math.floor(Math.random() * 256)) + ")";
          ctx.lineWidth = 5;
          ctx.stroke();
      }, 200);
    `;

    eval(functionText); */

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
        : 'bg-zinc-200 text-zinc-600'}"
      value="Send"
    />
  </form>
</div>

<style>
  #chat {
    height: calc(100% - 36px - 40px);
  }
</style>
