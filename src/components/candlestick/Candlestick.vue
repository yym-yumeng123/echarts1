<!-- k 线图 -->
<script setup>
import * as echarts from "echarts";
import { onMounted, ref } from "vue";
const myChart = ref(null);

onMounted(() => {
  const myEcharts = echarts.init(myChart.value);
  // 柱状图
  myEcharts.setOption({
    title: {
      text: "K 线图",
      link: "https://echarts.apache.org/zh/index.html",
      target: "self",
    },
    xAxis: {
      // type: "category",
      data: ["Mon", "Tue", "Wed", "Thu", "Fri", "Sat", "Sun"],
    },
    yAxis: {
      type: "value",
    },
    tooltip: {
      show: true,
      trigger: "axis",
      axisPointer: {
        type: "cross",
      },
    },
    series: [
      {
        type: "candlestick", // K 线图
        data: [
          [100, 200, 80, 150], // 开盘, 收盘, 最低, 最高
          [150, 220, 70, 200],
          [200, 250, 150, 220],
          [180, 120, 150, 200],
          [200, 300, 180, 250],
          [250, 280, 200, 250],
          [300, 220, 250, 300],
        ],
        itemStyle: {
          color: "#ec0000", // 阳线颜色
          color0: "#00da3c", // 阴线颜色
          borderColor: "#8A0000", // 阳线边框颜色
          borderColor0: "#008F28", // 阴线边框颜色
        },
        markPoint: {
          data: [
            { type: "max", name: "最大值", valueDim: "highest" }, // 最高值的维度, 默认为最后一个维度
            { type: "min", name: "最小值", valueDim: "lowest" }, // 最低值的维度, 默认为最后一个维度
            { type: "average", name: "平均值" },
          ],
        },
      },
      {
        type: "line",
        data: [150, 220, 250, 120, 300, 280, 220], // 收盘价
        smooth: true, // 平滑曲线
        markPoint: {
          data: [
            { name: "周最低", value: -2, xAxis: 1, yAxis: 260 },
          ],
        },
      },
    ],
  });
});
</script>

<template>
  <div ref="myChart" id="candlestick" style="width: 600px; height: 400px"></div>
</template>