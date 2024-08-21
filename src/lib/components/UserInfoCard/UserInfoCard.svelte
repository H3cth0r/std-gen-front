<!-- UserInfoCard.svelte -->
<script>
  import { Avatar } from '@skeletonlabs/skeleton';

  export let avatar = '';
  export let username = '';
  export let name = '';

</script>

<div class="card p-4 backdrop-blur-xl bg-white/60 shadow-xl rounded-lg">
  <div class="flex flex-row lg:flex-col items-center lg:mt-7 lg:mb-7">
    <Avatar
      src="https://images.unsplash.com/photo-1617296538902-887900d9b592?ixid=M3w0Njc5ODF8MHwxfGFsbHx8fHx8fHx8fDE2ODc5NzExMDB8&ixlib=rb-4.0.3&w=128&h=128&auto=format&fit=crop" 
      width="w-1/4" 
      rounded="rounded-full"
    />
    <div class="ml-7 lg:ml-0 flex flex-col items-start sm:items-start md:items-start lg:items-center xl:items-center">
      <h2 class="text-2xl font-bold mb-2">{username}</h2>
      <p class="text-gray-600">{name}</p>
    </div>
  </div>
</div>
