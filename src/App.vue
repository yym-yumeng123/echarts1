<script setup>
import Bar from "./components/Bar/Bar.vue";
import HorizontalBar from "./components/Bar/HorizontalBar.vue";
import GridBar from "./components/Bar/GridBar.vue";
import Pie from "./components/pie/Pie.vue";
import RingPie from "./components/pie/RingPie.vue";
import Line from "./components/line/BasicLine.vue";
import DataZoomLine from "./components/line/DataZoomLine.vue";
import MultipleLine from "./components/line/MultipleLine.vue";
import Scatter from "./components/scatter/Basicscatter.vue";
import Candlestick from "./components/candlestick/Candlestick.vue";
import Radar from "./components/radar/BasicRadar.vue";
import Funnel from "./components/funnel/Funnel.vue";
import Guage from "./components/guage/Guage.vue";
import Graph from "./components/graph/Graph.vue";
import Tree from "./components/tree/BasicTree.vue";
</script>

<template>
  <div>
    <Bar />
    <HorizontalBar />
    <GridBar />
    <Pie />
    <RingPie />
    <Line />
    <MultipleLine />
    <DataZoomLine />
    <Scatter />
    <Candlestick />
    <Radar />
    <Funnel />
    <Guage />
    <Graph />
    <Tree />
  </div>
</template>

<style scoped>
</style>
