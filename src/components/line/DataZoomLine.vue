<script setup>
import * as echarts from "echarts";
import { onMounted, ref } from "vue";
const myChart = ref(null);

onMounted(() => {
  const myEcharts = echarts.init(myChart.value);
  // 柱状图
  myEcharts.setOption({
    title: {
      text: "折线图/曲线图-区域缩放",
      link: "https://echarts.apache.org/zh/index.html",
      target: "self",
    },
    // dataZoom: 区域缩放
    dataZoom: [
      {
        type: "slider", // 滑动条 slider | inside
        show: true,
        xAxisIndex: [0], // x 轴索引
        start: 1,
        end: 100,
        filterMode: "none", // filterMode: 'filter' | 'weakFilter' | 'empty' | 'none' 默认值为'filter'，表示『数据窗口范围的数据』经过本过滤器后，将会被『保留下来』。
      },
      {
        type: "slider", // 滑动条 slider | inside
        show: true,
        yAxisIndex: [0],
        start: 1,
        end: 100,
        filterMode: "none",
      },
    ],
    legend: {
    },
    tooltip: {
      trigger: "axis",
    },
    xAxis: {
      type: "category",
      data: ["周一", "周二", "周三", "周四", "周五", "周六", "周日"],
    },
    yAxis: {
      type: "value",
    },
    // 系列: 对应数组, 配置图标的类型
    series: [
      {
        name: "访问来源",
        type: "line", // 折线图
        data: [150, 230, 224, 218, 135, 147, 260],
        smooth: true, // 平滑曲线
        areaStyle: {
          color: new echarts.graphic.LinearGradient(0, 0, 0, 1, [
            {
              offset: 0,
              color: "rgba(128, 255, 165)",
            },
            {
              offset: 1,
              color: "rgba(1, 191, 236)",
            },
          ]),
        }, // 区域填充
        markPoint: {
          data: [
            { type: "max", name: "最大值" },
            { type: "min", name: "最小值" },
          ],
        },
        markLine: {
          data: [{ type: "average", name: "平均值" }],
        },
      },
    ],
  });
});
</script>

<template>
  <div ref="myChart" id="line1" style="width: 600px; height: 400px"></div>
</template>
