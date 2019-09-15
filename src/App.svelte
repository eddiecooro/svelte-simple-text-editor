<script>
  let html;
  let js;
  $: {
    const script = document.createElement("script");
    script.innerHTML = js;
    document.querySelector("head").appendChild(script);
  }
</script>

<style>
  :global(body) {
    padding: 0;
  }
  style {
    display: block;
  }
  [contenteditable] {
    font-family: monospace;
    white-space: pre;
    padding: 10px;
  }
  .container {
    height: 100vh;
    width: 100vw;
    display: flex;
    flex-direction: row;
  }
  .editors {
    display: flex;
    flex-direction: column;
    flex: 1;
  }
  .results {
    flex: 1;
    border: medium solid red;
  }
  .editor {
    flex: 1;
    border: thick solid black;
  }
</style>

<div class="container">
  <div class="editors">
    <div contenteditable bind:textContent={html} class="editor html" />
    <style contenteditable class="editor css">

    </style>
    <div contenteditable bind:textContent={js} class="editor js" />
  </div>
  <div class="results">
    {@html html}
  </div>
</div>
