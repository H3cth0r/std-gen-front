<script>
  import { Accordion, AccordionItem } from '@skeletonlabs/skeleton';
  import { GroupTable } from '$lib/components';
  export let groups_list = [
    { "group_name" : "Group A", "id": "2fw2ddf2g"},
    { "group_name" : "Group B", "id": "fa3ffsvvv2"},
  ];
</script>

<Accordion autocollapse>
  {#each groups_list as row, i}
    {#if i == 0}
      <AccordionItem open>
        <svelte:fragment slot="lead"><i class="fa-solid fa-clock text-xl w-6 text-center"></svelte:fragment>
        <svelte:fragment slot="summary"><span class="font-bold">{row.group_name}</span></svelte:fragment>
        <svelte:fragment slot="content">
          <GroupTable 
            group_id={row.id}
          />
        </svelte:fragment>
      </AccordionItem>
    {:else}
      <AccordionItem>
        <svelte:fragment slot="lead"><i class="fa-solid fa-clock text-xl w-6 text-center"></svelte:fragment>
        <svelte:fragment slot="summary"><span class="font-bold">{row.group_name}</span></svelte:fragment>
        <svelte:fragment slot="content">
          <GroupTable 
            group_id={row.id}
          />
        </svelte:fragment>
      </AccordionItem>
    {/if}
  {/each}
</Accordion>

<style>
</style>
