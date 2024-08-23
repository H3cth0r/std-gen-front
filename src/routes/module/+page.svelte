<script>
  import { SlideBar, ModuleInfo } from '$lib/components';

  function createRange(start, end) {
    return Array.from({ length: end - start + 1 }, (_, i) => start + i);
  }
  let numbers = createRange(1, 20);
</script>

<div class="card flex flex-row h-[92vh] w-screen">
  <SlideBar />
  <div class="flex flex-col flex-1 overflow-y-auto items-center justify-center p-4 ">
      <div class="border rounded-lg border-zinc-400/50 p-6 w-[90%] h-[90%] mb-4">
        <div class="w-full h-full bg-red-400">
          <ModuleInfo />
        </div>
      </div>
  </div>
</div>

<style>
  .card {
    /* Your card styling here */
  }
</style>

