<!-- PlanCard.svelte -->
<script lang="ts">
  export let title: string;
  export let features: string[];
  export let price: string;
  export let isPopular: boolean = false;
</script>

<div class="card p-6 shadow-xl {isPopular ? 'border-4 border-primary-500' : ''} bg-white w-80 h-[40rem] flex flex-col">
  <header class="mb-4 flex-none h-20"> <!-- Fixed height for header -->
    <h3 class="h3">{title}</h3>
    {#if isPopular}
      <span class="badge variant-filled-primary mt-2">Most Popular</span>
    {/if}
  </header>
  <ul class="list mb-4 flex-grow overflow-y-auto"> <!-- Allow scrolling if too many features -->
    {#each features as feature}
      <li class="flex items-center gap-2 mb-2">
        <span class="text-green-500 flex-shrink-0">✓</span>
        <span>{feature}</span>
      </li>
    {/each}
  </ul>
  <footer class="flex flex-col items-center mt-auto pt-4"> <!-- Added padding top -->
    <p class="h2 mb-2">{price}</p>
    <button class="btn variant-filled-primary w-full">Select Plan</button>
  </footer>
</div>
