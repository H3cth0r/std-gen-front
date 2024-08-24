<script>
  import { SlideBar, ModuleInfo, StepperButton } from '$lib/components';
  function createRange(start, end) {
    return Array.from({ length: end - start + 1 }, (_, i) => start + i);
  }
  let numbers = createRange(1, 20);
</script>

<div class="card flex flex-row h-[92vh] w-screen">
  <SlideBar />
  <div class="flex flex-col flex-1 relative">
    <div class="absolute inset-0 overflow-y-auto p-0 sm:p-4 flex flex-col">
      <div class="flex-grow border rounded-lg border-zinc-400/50 p-2 sm:p-6 w-full h-auto sm:w-[90%] sm:h-[90%] sm:m-auto">
        <div class="w-full h-full">
          <ModuleInfo />
        </div>
      </div>
      <div  class="flex w-full p-2 justify-center">
        <StepperButton />
      </div>
    </div>
  </div>
</div>

<style>
  .card {
    /* Your card styling here */
  }
</style>
