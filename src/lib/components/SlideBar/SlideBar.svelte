<script>
  import { slide } from 'svelte/transition';
  export let isOpen = false;
  export let direction = 'left'; // 'left' or 'right'

  const toggleSidebar = () => {
    isOpen = !isOpen;
  };

  $: sidebarPosition = direction === 'left' ? 'left-0' : 'right-0';
  $: translateX = direction === 'left' ? '-translate-x-full' : 'translate-x-full';

  // Calculate button position based on sidebar state
  $: buttonPosition = isOpen
    ? direction === 'left'
      ? 'left-64'
      : 'right-64'
    : direction === 'left'
    ? 'left-0'
    : 'right-0';
</script>

<div class="relative h-[92vh]">
  <div
    class={`card absolute top-0 ${sidebarPosition} h-full w-64 transition-transform duration-300 ease-in-out z-20 ${
      isOpen ? '' : translateX
    }`}
  >
    <div class="p-4">
      <!-- Options -->
      <h2 class="text-xl font-bold mb-4">Sidebar Options</h2>
      <ul>
        <li class="mb-2">Option 1</li>
        <li class="mb-2">Option 2</li>
        <li class="mb-2">Option 3</li>
      </ul>
    </div>
  </div>
  <button
    on:click={toggleSidebar}
    type="button"
    class={`btn-icon !bg-transparent fixed ${buttonPosition} top-[calc(50%-4vh)] p-2 focus:outline-none z-30 transition-all duration-300 ease-in-out`}
  >
    <svg
      xmlns="http://www.w3.org/2000/svg"
      class="h-6 w-6"
      fill="none"
      viewBox="0 0 24 24"
      stroke="currentColor"
    >
      <path
        stroke-linecap="round"
        stroke-linejoin="round"
        stroke-width="2"
        d={isOpen
          ? direction === 'left'
            ? "M15 19l-7-7 7-7"
            : "M9 5l7 7-7 7"
          : direction === 'left'
            ? "M9 5l7 7-7 7"
            : "M15 19l-7-7 7-7"}
      />
    </svg>
  </button>
</div>
