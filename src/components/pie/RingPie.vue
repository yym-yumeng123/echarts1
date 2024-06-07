<script setup>
import * as echarts from "echarts";
import { onMounted, ref } from "vue";
const myChart = ref(null);

onMounted(() => {
  const myEcharts = echarts.init(myChart.value);
  // 柱状图
  myEcharts.setOption({
    title: {
      text: "环形饼状图",
      link: "https://echarts.apache.org/zh/index.html",
      target: "self",
    },
    tooltip: {
      show: true,
      trigger: "item",
      formatter: "{a} <br/>{b}: {c} ({d}%)",
    },
    legend: {
      left: 'left',
      top: 40,
      orient: "vertical",
      data: ["视频广告", "联盟广告", "邮件营销", "直接访问", "搜索引擎"],
    },
    // 系列: 对应数组, 配置图标的类型
    series: [
      {
        name: "访问来源",
        type: "pie", // 饼状图
        radius: ["50%", "70%"], // 第一项内半径, 第二项外半径
        label: {
          // show: false, // 不显示标签
          position: "outside", // 标签的位置 outside, inside, center
        },
        // roseType: "area", // 面积模式
        data: [
          { value: 235, name: "视频广告" },
          { value: 274, name: "联盟广告" },
          { value: 310, name: "邮件营销" },
          { value: 335, name: "直接访问" },
          { value: 400, name: "搜索引擎" },
        ],
      },
    ],
  });
});
</script>

<template>
  <div ref="myChart" id="pie2" style="width: 600px; height: 400px"></div>
</template>
