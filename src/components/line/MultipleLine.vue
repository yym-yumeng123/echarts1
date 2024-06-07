<script setup>
import * as echarts from "echarts";
import { onMounted, ref } from "vue";
const myChart = ref(null);

onMounted(() => {
  const myEcharts = echarts.init(myChart.value);
  // 柱状图
  myEcharts.setOption({
    title: {
      text: "多条折线图/曲线图",
      link: "https://echarts.apache.org/zh/index.html",
      target: "self",
    },
    legend: {
    },
    xAxis: {
      type: "category",
      data: ["周一", "周二", "周三", "周四", "周五", "周六", "周日"],
    },
    yAxis: {
      type: "value",
    },
    tooltip: {
      trigger: "axis",
    },
    // 系列: 对应数组, 配置图标的类型
    series: [
      {
        name: "访问来源",
        type: "line", // 折线图
        data: [150, 230, 224, 218, 135, 147, 260],
        areaStyle: {}, // 区域填充样式
        // 选中高亮
        emphasis: {
          focus: "series",
        },
      },
      {
        name: "广告",
        type: "line", // 折线图
        data: [140, 20, 200, 250, 180, 120, 300],
        smooth: true, // 平滑曲线
        // stack: "总量", // 数据的堆叠
        areaStyle: {}, // 区域填充样式
      },
    ],
  });
});
</script>

<template>
  <div ref="myChart" id="line1" style="width: 600px; height: 400px"></div>
</template>
