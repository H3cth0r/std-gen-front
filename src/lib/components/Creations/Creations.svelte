<!-- Creations.svelte -->
<script>
  import { ModuleCard } from '$lib/components';
  const modules = [
    { title: "Module 1", activities: 5, days: 7, date: "2023-08-01", username: "user1", isPublic: true },
    { title: "Module 2", activities: 3, days: 5, date: "2023-08-05", username: "user2", isPublic: false },
    { title: "Module 2", activities: 3, days: 5, date: "2023-08-05", username: "user2", isPublic: false },
    { title: "Module 2", activities: 3, days: 5, date: "2023-08-05", username: "user2", isPublic: false },
  ];
</script>

<div class="container mx-auto px-4 w-full h-full">
  <div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-1 lg:grid-cols-1 xl:grid-cols-3 gap-4">
    {#each modules as module}
      <ModuleCard {...module} />
    {/each}
  </div>
</div>
