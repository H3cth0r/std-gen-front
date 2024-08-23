<script>
</script>

<div class="h-full w-full flex flex-col">
  <div class="h-[10%] w-full bg-green-400">
    <h1 class="h1">Title</h1>
  </div>
  <div class="h-[90%] w-full bg-blue-400 overflow-y-auto">
    <!-- Grid 2x2 on large devices, 1x4 on small devices -->
    <div class="grid grid-cols-1 md:grid-cols-2 md:grid-rows-2 gap-4 p-4 h-full">
      <div class="bg-gray-200 p-4 rounded-lg md:h-full overflow-y-auto">
        <!-- Initial Prompt -->
        <h2 class="text-lg font-semibold mb-2">Initial Prompt</h2>
        <p>Content for Initial Prompt</p>
      </div>
      <div class="bg-gray-200 p-4 rounded-lg md:h-full overflow-y-auto">
        <!-- General Information -->
        <h2 class="text-lg font-semibold mb-2">General Information</h2>
        <p>Content for General Information</p>
      </div>
      <div class="bg-gray-200 p-4 rounded-lg md:h-full overflow-y-auto">
        <!-- Groups -->
        <h2 class="text-lg font-semibold mb-2">Groups</h2>
        <p>Content for Groups</p>
      </div>
      <div class="bg-gray-200 p-4 rounded-lg md:h-full overflow-y-auto">
        <!-- Many buttons -->
        <h2 class="text-lg font-semibold mb-2">Buttons</h2>
        <div class="flex flex-wrap gap-2">
          <button class="bg-blue-500 text-white px-3 py-1 rounded">Button 1</button>
          <button class="bg-blue-500 text-white px-3 py-1 rounded">Button 2</button>
          <button class="bg-blue-500 text-white px-3 py-1 rounded">Button 3</button>
        </div>
      </div>
    </div>
  </div>
</div>

<style>
</style>
