<!-- ModuleCard.svelte -->
<script lang="ts">
  import { Avatar } from '@skeletonlabs/skeleton';
  import { goto } from '$app/navigation';

  export let title = "";
  export let activities = 0;
  export let days = 0;
  export let date = "";
  export let username = "";
  export let isPublic = false;

</script>

<a class="card p-4" href="/module">
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
  </section>
  
  <footer class="card-footer flex justify-between items-center">
    <span></span>
    <button type="button" class="btn btn-sm !bg-transparent" on:click={() => {goto("/")}} >
      <Avatar 
        src="https://images.unsplash.com/photo-1617296538902-887900d9b592?ixid=M3w0Njc5ODF8MHwxfGFsbHx8fHx8fHx8fDE2ODc5NzExMDB8&ixlib=rb-4.0.3&w=128&h=128&auto=format&fit=crop" 
        width="w-10" 
        rounded="rounded-full" 
        border="border-4 border-surface-300-600-token hover:!border-primary-500"
        cursor="cursor-pointer"
      />
    </button>
  </footer>
</a>
