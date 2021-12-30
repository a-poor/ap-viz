<!-- src/routes/index.svelte -->
<style>
  .chart :global(div) {
    font: 10px sans-serif;
    background-color: steelblue;
    text-align: right;
    padding: 3px;
    margin: 1px;
    color: white;
  }
</style>

<svelte:head>
  <title>AP Viz</title>
  <style>
    html,
    body {
      margin: 0;
      padding: 0;
      height: 100%;
    }
  </style>
</svelte:head>

<div class="mdc-typography--headline2">Welcome to SvelteKit</div>

<div bind:this={el} class="chart" />

<script lang="ts">
  import { onMount } from 'svelte';
  import * as d3 from 'd3';
  var data = [30, 86, 168, 281, 303, 365];

  let el;

  onMount(() => {
    d3.select(el)
      .selectAll('div')
      .data(data)
      .enter()
      .append('div')
      .style('width', function (d) {
        return d + 'px';
      })
      .text((d: String) => d);
  });
</script>
