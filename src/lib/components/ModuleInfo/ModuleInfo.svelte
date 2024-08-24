<script>
  import PromptSection from './PromptSection.svelte';
  import Groups from './Groups.svelte';
  import Information from './Information.svelte';
  import Actions from './Actions.svelte';
</script>

<div class="h-full w-full flex flex-col">
  <div class="h-[10%] w-full bg-green-400 flex items-center">
    <h1 class="h1">Title</h1>
  </div>
  <div class="h-[90%] w-full bg-blue-400 overflow-y-auto">
    <!-- Grid 2x2 on large devices, 1x4 on small devices -->
    <div class="grid grid-cols-1 md:grid-cols-2 md:grid-rows-2 gap-2 h-full">
      <div class="bg-gray-200 p-4 rounded-lg md:h-full md:overflow-y-auto">
        <!-- Initial Prompt -->
        <PromptSection />
      </div>
      <div class="bg-gray-200 p-4 rounded-lg md:h-full md:overflow-y-auto">
        <!-- General Information -->
        <Information />
      </div>
      <div class="bg-gray-200 p-4 rounded-lg md:h-full md:overflow-y-auto">
        <!-- Groups -->
        <Groups />
      </div>
      <div class="bg-gray-200 p-4 rounded-lg md:h-full md:overflow-y-auto">
        <!-- Many buttons -->
        <Actions />
      </div>
    </div>
  </div>
</div>

<style>
</style>
