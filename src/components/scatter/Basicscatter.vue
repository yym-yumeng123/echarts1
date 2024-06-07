<script setup>
import * as echarts from "echarts";
import { onMounted, ref } from "vue";
const myChart = ref(null);

onMounted(() => {
  const myEcharts = echarts.init(myChart.value);
  // 柱状图
  myEcharts.setOption({
    title: {
      text: "散点图",
      link: "https://echarts.apache.org/zh/index.html",
      target: "self",
    },
    xAxis: {
      type: "value",
    },
    yAxis: {
      type: "value",
    },
    legend: {
      data: ["散点"],
    },
    // 系列: 对应数组, 配置图标的类型
    series: [
      {
        name: "散点",
        type: "scatter", // 散点图
        symbolSize: 20, // 散点的大小
        tootip: {
          show: true,
          trigger: "item",
        },
        // x, y 轴的数据
        data: [
          [10.0, 8.04],
          [8.0, 6.95],
          [13.0, 7.58],
          [9.0, 8.81],
          [11.0, 8.33],
          [14.0, 9.96],
          [6.0, 7.24],
          [4.0, 4.26],
          [12.0, 10.84],
          [7.0, 4.82],
          [5.0, 5.68],
        ],
        // 散点的颜色
        color: {
          // 线性渐变
          type: "linear",
          // 相当于在图形包围盒中的坐标, 0, 0 表示左下角, 1, 1 表示右上角
          x: 0,
          y: 0,
          x2: 1,
          y2: 0,
          // 颜色的渐变
          colorStops: [
            {
              offset: 0,
              color: "red", // 0% 处的颜色
            },
            {
              offset: 1,
              color: "blue", // 100% 处的颜色
            },
          ],
        },
        // 鼠标移入高亮的样式
        emphasis: {
          itemStyle: {
            borderColor: "black",
            borderWidth: 2,
          }
        },
      },
    ],
  });

})
</script>

<template>
  <div ref="myChart" id="scatter1" style="width: 600px; height: 400px"></div>
</template>