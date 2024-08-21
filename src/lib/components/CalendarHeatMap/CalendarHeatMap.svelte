<script>
  import { onMount } from 'svelte';
  import SvelteHeatmap from 'svelte-heatmap';
  import { getModeUserPrefers } from '@skeletonlabs/skeleton';

  // Props
  export let data = [];
  export let allowOverflow = false;
  export let cellGap = undefined;
  export let cellRadius = undefined;
  export let cellSize = 10; // Default cell size
  export let colors = ['#c6e48b', '#7bc96f', '#239a3b', '#196127'];
  export let dayLabelWidth = 20; // Default day label width
  export let dayLabels = ['', 'Mon', '', 'Wed', '', 'Fri', ''];
  export let fontColor = '#333';
  export let fontFamily = 'sans-serif';
  export let fontSize = 8;
  export let emptyColor = '#ebedf0'; // Default empty color
  export let monthGap = 2; // Default month gap
  export let monthLabelHeight = 20; // Default month label height
  export let monthLabels = ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun', 'Jul', 'Aug', 'Sep', 'Oct', 'Nov', 'Dec'];
  export let startDate = undefined;
  export let endDate = undefined;
  export let view = 'yearly';
  export let width = '100%'; // Default width as percentage
  export let height = '100%'; // Default height as percentage

  let heatmapContainer;
  let heatmap;
  let currentTheme;

  $: currentTheme = getModeUserPrefers();
  $: fontColor = currentTheme ? '#333333' : '#ffffff';
  $: emptyColor = currentTheme ? '#ebedf0' : '#2a2a2a';


  onMount(() => {
    console.log("Mounting heatmap component");
    console.log("Data:", data);
    console.log(getModeUserPrefers());
    
    if (!startDate) {
      startDate = new Date(new Date().getFullYear(), 0, 1); // Start of current year
    }
    if (!endDate) {
      endDate = new Date(new Date().getFullYear(), 11, 31); // End of current year
    }

    try {
      heatmap = new SvelteHeatmap({
        target: heatmapContainer,
        props: {
          data,
          allowOverflow,
          cellGap,
          cellRadius,
          cellSize,
          colors,
          dayLabelWidth,
          dayLabels,
          fontColor,
          fontFamily,
          fontSize,
          emptyColor,
          monthGap,
          monthLabelHeight,
          monthLabels,
          startDate,
          endDate,
          view,
        },
      });
      console.log("Heatmap created successfully");
    } catch (error) {
      console.error("Error creating heatmap:", error);
    }

    return () => {
      if (heatmap) {
        heatmap.$destroy();
      }
    };
  });
</script>

<div class="heatmap-wrapper" style="width: {width}; height: {height}; position: relative;">
  <div bind:this={heatmapContainer} style="width: 100%; height: 100%; overflow: auto;">
    {#if !data || data.length === 0}
      <p>No data available for the heatmap.</p>
    {/if}
  </div>
</div>

<style>
  .heatmap-wrapper {
    overflow: hidden;
  }
  .heatmap-wrapper :global(svg) {
    display: block;
    width: 100%;
    height: 100%;
  }
  .heatmap-wrapper :global(.heatmap-month-labels) {
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    z-index: 1;
  }
</style>
