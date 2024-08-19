<!-- UserInfoCard.svelte -->
<script>
  import { Avatar } from '@skeletonlabs/skeleton';
  import { CalendarHeatMap } from '$lib/components';

  export let avatar = '';
  export let username = '';
  export let name = '';

  const heatmapData = [
    { date: '2024-01-01', value: 5 },
    { date: '2024-01-02', value: 10 },
  ];
</script>

<div class="card p-4 backdrop-blur-xl bg-white/60 shadow-xl rounded-lg">
  <div class="flex flex-col items-center">
    <Avatar src="https://images.unsplash.com/photo-1617296538902-887900d9b592?ixid=M3w0Njc5ODF8MHwxfGFsbHx8fHx8fHx8fDE2ODc5NzExMDB8&ixlib=rb-4.0.3&w=128&h=128&auto=format&fit=crop" width="w-32" rounded="rounded-full" />
    <h2 class="text-2xl font-bold mb-2">{username}</h2>
    <p class="text-gray-600">{name}</p>
    <div class="flex flex-col items-center justify-center h-60 w-full">
      <CalendarHeatMap
        data={heatmapData}
        cellSize={15}
        cellRadius="3px"
        fontColor="#666"
        view="yearly"
        width="100%"
        height="50%"
      />
    </div>
  </div>
</div>
