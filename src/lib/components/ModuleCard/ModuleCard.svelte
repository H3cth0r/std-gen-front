<!-- ModuleCard.svelte -->
<script lang="ts">
  export let title = "";
  export let activities = 0;
  export let days = 0;
  export let date = "";
  export let username = "";
  export let isPublic = false;

  function handleOptions() {
    // Handle options menu
    console.log("Options clicked");
  }

</script>


<a class="card p-4">
  <header class="card-header flex justify-between items-center">
    <h3 class="h3">{title}</h3>
    {#if isPublic}
      <span class="badge bg-gradient-to-br variant-gradient-secondary-tertiary">Public</span>
    {:else}
      <span class="badge bg-gradient-to-br variant-gradient-tertiary-primary">Private</span>
    {/if}
  </header>
  
  <section class="p-4">
    <p><span class="font-semibold">Activities:</span> {activities}</p>
    <p><span class="font-semibold">Days:</span> {days}</p>
    <p><span class="font-semibold">Date:</span> {date}</p>
    <p><span class="font-semibold">Created by:</span> {username}</p>
  </section>
  
  <footer class="card-footer flex justify-between items-center">
    <span></span>
    <button type="button" class="btn btn-sm !bg-transparent" on:click={handleOptions} >
      <span class="text-xl">⋮</span>
    </button>
  </footer>
</a>
