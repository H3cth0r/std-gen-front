<script lang="ts">
  import { popup } from '@skeletonlabs/skeleton';
  import type { PopupSettings } from '@skeletonlabs/skeleton';
  import { ListBox, ListBoxItem } from '@skeletonlabs/skeleton';
  import { onMount } from 'svelte';

  export let minHeight = '100px';
  export let maxHeight = '300px';
  export let placeholder = 'Write a devotional about ...';
  
  let textarea: HTMLTextAreaElement;
  let isEmpty = true;
  let containerDiv: HTMLDivElement;
  let comboboxValue: string;
  
  const popupCombobox: PopupSettings = {
    event: 'click',
    target: 'popupCombobox',
    placement: 'top',
    closeQuery: '.listbox-item'
  };

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

<div class="flex flex-col sm:flex-row space-y-4 sm:space-y-0 sm:space-x-4 mb-4">
  <div class="w-full sm:w-auto">
    <button class="btn variant-filled w-full sm:w-48 justify-between" use:popup={popupCombobox}>
      <span class="capitalize">{comboboxValue ?? 'Select'}</span>
      <span>↑</span>
    </button>
    <div class="card w-full sm:w-48 shadow-xl py-2" data-popup="popupCombobox">
      <ListBox rounded="rounded-none">
        <ListBoxItem bind:group={comboboxValue} name="audience" value="adults">Adults</ListBoxItem>
        <ListBoxItem bind:group={comboboxValue} name="audience" value="kids">Kids</ListBoxItem>
        <ListBoxItem bind:group={comboboxValue} name="audience" value="teens">Teens</ListBoxItem>
        <ListBoxItem bind:group={comboboxValue} name="audience" value="olds">Olds</ListBoxItem>
      </ListBox>
      <div class="arrow bg-surface-100-800-token" />
    </div>
  </div>
  
  <div class="w-full sm:w-auto">
    <div class="input-group input-group-divider grid-cols-[1fr_auto]">
      <input type="text" placeholder="Number of days" class="w-full" />
      <div class="input-group-shim">days</div>
    </div>
  </div>
</div>

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
