<script>
  import CodeMirror, { basicSetup } from "./codemirror.svelte";
  import { javascript } from "@codemirror/lang-javascript";
  import { EditorState } from "@codemirror/state";
  let store;

  function changeHandler({ detail: { tr } }) {
    console.log("change", tr.changes.toJSON());
  }
</script>

<div class="h-full flex">
  <div
    class="box-border border-r border-zinc-200 h-full w-1/2 overflow-y-scroll"
  >
    CODE RESULT
    <CodeMirror
      doc={"var c = document.getElementById('myCanvas');\nvar ctx = c.getContext('2d');"}
      bind:docStore={store}
      extensions={[basicSetup, javascript(), EditorState.readOnly.of(true)]}
      on:change={changeHandler}
    />
  </div>

  <div class="border-r border-zinc-200 h-full w-1/2">
    <div class="box-border border-b border-zinc-200 h-1/2 w-full">PROMPT</div>
    <div class="box-border border-b border-zinc-200 h-1/2 w-full">
      VISUAL RESULT
    </div>
  </div>
</div>
