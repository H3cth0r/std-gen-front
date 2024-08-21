<script lang="ts">
  import { Avatar } from '@skeletonlabs/skeleton';
  import { getModalStore } from '@skeletonlabs/skeleton';
  import type { ModalSettings } from '@skeletonlabs/skeleton';
  const modalStore = getModalStore();

  export let onRemoveGroup = (id: str, r: boolean) => {
    console.log("This is the bool: ", r);
    console.log("id:", id);
  }
  let userToRemove;
  export let onRemoveUser = (id: str, r: boolean) => {
    console.log("This is the bool: ", r);
    console.log("username: ", id);
  }

  const confirmRemoveGroupModal: ModalSettings = {
      type: 'confirm',
      title: 'Please Confirm',
      body: 'Are you sure you wish to proceed?',
      response: (r: boolean) => {
        onRemoveGroup(group_id, r); 
      },
  };
  const confirmRemoveUserModal: ModalSettings = {
      type: 'confirm',
      title: 'Please Confirm',
      body: 'Are you sure you wish to proceed?',
      response: (r: boolean) => {
        onRemoveUser(userToRemove, r); 
      },
  };

  export let group_id = "pipipi";
  export let group_list = [
    { "username": "Pedro", "progress": 100 },
    { "username": "deadpool", "progress": 55 },
    { "username": "thor", "progress": 25 },
  ];
</script>

<div class="w-full flex flex-row justify-end">
  <button 
    type="button" 
    class="btn variant-filled-error"
    on:click={() => {
      modalStore.trigger(confirmRemoveGroupModal);
    }}
  >Remove</button>
</div>

<div class="table-container">
  <table class="table table-hover">
		<thead>
			<tr>
				<th>User</th>
				<th>Progress</th>
				<th>Completed</th>
				<th>Remove</th>
			</tr>
		</thead>
    <tbody>
      {#each group_list as row, i}
        <tr>
          <td class="flex flex-row items-center">
            <Avatar 
              src="https://images.unsplash.com/photo-1617296538902-887900d9b592?ixid=M3w0Njc5ODF8MHwxfGFsbHx8fHx8fHx8fDE2ODc5NzExMDB8&ixlib=rb-4.0.3&w=128&h=128&auto=format&fit=crop" 
              width="w-14" 
              rounded="rounded-full" 
            />
            <a class="pl-5" href="/">
            {row.username}
            </a>
          </td>
          <td>{row.progress}%</td>
          <td>
            {#if row.progress >= 100}
              <span class="badge variant-filled-success">Completed</span> 
            {:else if row.progress >= 50}
              <span class="badge variant-filled-warning">In Progress</span> 
            {:else}
              <span class="badge variant-filled-error">Incomplete</span> 
            {/if}
          </td>
          <td>
            <button 
              type="button" 
              class="btn variant-filled-error"
              on:click={() => {
                userToRemove = row.username;
                modalStore.trigger(confirmRemoveUserModal);
              }}
            >Remove</button>
          </td>
        </tr>
      {/each}
    </tbody>
  </table>
</div>

<style>
</style>
