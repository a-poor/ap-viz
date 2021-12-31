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

	.chart{
		min-width: 375px;
		margin: 15px auto;
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

<div class="mdc-typography--headline2" style="margin-top: 15px;">Welcome to SvelteKit</div>

<div bind:this={el} class="chart" />

<script lang="ts">
  import { onMount } from 'svelte';
  import * as d3 from 'd3';
  import timelineData from './data/timeline.json';

  let el;

	const width = 500;
	const height = 200;
	const margin = {
		top: 20,
		right: 20,
		bottom: 30,
		left: 50,
	};

	const xScale = d3.scaleTime()
										.domain([])
										.range([0, width - margin.left - margin.right]);
	const yScale = d3.scaleOrdinal()
										.domain([])
										.range([0, width - margin.left - margin.right]);

  onMount(() => {
		const svg = d3.select(el)
			.append('svg')
			.attr('width', '100%')
			.attr('margin', 'auto')
			.attr("viewBox", [0, 0, width, height])
			.style("border", "1px solid black");


    svg.append('g')
      .selectAll('rect')
      .data(timelineData.events)
      .enter()
      .append('circle')
      .attr('cx', (_, i) => i * 20 + 100)
			.attr('cy', (_, i) => i * 10 + 10)
			.attr('r', 5)
      .text((d: String) => d);
  });
</script>
