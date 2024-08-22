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
      <Tab bind:group={tabSet} name="recents" value={0}>
        <span>Recents</span>
      </Tab>
      <Tab bind:group={tabSet} name="creations" value={1}>
        <span>Creations</span>
      </Tab>
      <Tab bind:group={tabSet} name="groups" value={2}>
        <span>Groups</span>
      </Tab>
      <Tab bind:group={tabSet} name="account" value={3}>
        <span>Account</span>
      </Tab>
      
      <!-- Tab Panels -->
      <svelte:fragment slot="panel">
        {#if tabSet === 0}
          <Creations />
        {:else if tabSet === 1}
          <Creations />
        {:else if tabSet === 2}
          <GroupsList />
        {:else if tabSet === 3}
          <p>Account</p>
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
