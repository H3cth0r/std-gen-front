<!-- +page.svelte -->
<script>
  import { TabGroup, Tab } from '@skeletonlabs/skeleton';
  import { UserInfoCard } from '$lib/components';
  import { Creations } from "$lib/components";
  import { GroupsList } from '$lib/components';

  let tabSet = 0;
  let avatar = 'path/to/avatar.jpg';
  let username = 'JohnDoe';
  let name = 'John Doe';

</script>

<div class="card flex flex-col md:flex-row p-4 h-[92vh] ">
  <div class="w-full md:w-1/3 md:pr-4 mb-4 md:mb-0">
    <UserInfoCard {avatar} {username} {name} />
  </div>
  <div class="card w-full md:w-2/3 backdrop-blur-xl bg-white/60 rounded-lg shadow-xl p-4 overflow-y-auto">
    <TabGroup>
      <Tab bind:group={tabSet} name="creations" value={0}>
        <span>Creations</span>
      </Tab>
      <Tab bind:group={tabSet} name="groups" value={1}>
        <span>Groups</span>
      </Tab>
      <Tab bind:group={tabSet} name="classes" value={2}>
        <span>Classes</span>
      </Tab>
      <Tab bind:group={tabSet} name="stats" value={3}>
        <span>Stats</span>
      </Tab>
      <Tab bind:group={tabSet} name="account" value={4}>
        <span>Account</span>
      </Tab>
      
      <!-- Tab Panels -->
      <svelte:fragment slot="panel">
        {#if tabSet === 0}
          <Creations />
        {:else if tabSet === 1}
          <GroupsList />
        {:else if tabSet === 2}
          <p>Classes content will go here</p>
        {:else if tabSet === 3}
          <p>Stats content will go here</p>
        {:else if tabSet === 4}
          <p>Account content will go here</p>
        {/if}
      </svelte:fragment>
    </TabGroup>
  </div>
</div>

<style>
  :global(:root) {
    --app-bar-height: 64px; /* Adjust this value to match your AppBar height */
  }
</style>
