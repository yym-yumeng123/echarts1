<script setup>
import Bar from "./components/Bar/Bar.vue";
import HorizontalBar from "./components/Bar/HorizontalBar.vue";
import GridBar from "./components/Bar/GridBar.vue";
import Pie from "./components/pie/Pie.vue";
import RingPie from "./components/pie/RingPie.vue";
import Line from "./components/line/BasicLine.vue";
import MultipleLine from "./components/line/MultipleLine.vue";
import Scatter from "./components/scatter/Basicscatter.vue";
import Candlestick from "./components/candlestick/Candlestick.vue";
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
    <Scatter />
    <Candlestick />
  </div>
</template>

<style scoped>
</style>
