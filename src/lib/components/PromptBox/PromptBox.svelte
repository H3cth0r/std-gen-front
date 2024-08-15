<script lang="ts">
  import { onMount } from 'svelte';

  export let minHeight = '100px';
  export let maxHeight = '300px';
  export let placeholder = 'Write a devotional about ...';

  let textarea: HTMLTextAreaElement;
  let isEmpty = true;
  let containerDiv: HTMLDivElement;

  function adjustTextareaHeight() {
    if (textarea.value.trim() === '') {
      containerDiv.style.height = minHeight;
      isEmpty = true;
    } else {
      containerDiv.style.height = maxHeight;
      isEmpty = false;
    }
    textarea.style.height = '100%';
  }

  function handleInput() {
    adjustTextareaHeight();
  }

  function sendPrompt() {
    console.log('Sending prompt:', textarea.value);
  }

  onMount(() => {
    adjustTextareaHeight();
  });
</script>

<div class="relative textarea-container" bind:this={containerDiv}>
  <textarea
    bind:this={textarea}
    class="textarea w-full pr-16"
    class:empty={isEmpty}
    {placeholder}
    on:input={handleInput}
  />
  <button
    class="btn variant-filled absolute bottom-2 right-2"
    on:click={sendPrompt}
  >
    Send
  </button>
</div>

<style>
  .textarea-container {
    position: relative;
    transition: height 0.3s ease;
  }

  .textarea {
    resize: none;
    overflow-y: auto;
    height: 100%;
    width: 100%;
    position: absolute;
    top: 0;
    left: 0;
  }
</style>
