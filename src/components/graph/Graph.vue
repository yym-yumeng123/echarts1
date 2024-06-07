<!-- 关系图 -->

<script setup>
import * as echarts from "echarts";
import { onMounted, ref } from "vue";
const myChart = ref(null);

onMounted(() => {
  const myEcharts = echarts.init(myChart.value);
  // 关系图
  myEcharts.setOption({
    title: {
      text: "关系图",
      link: "https://echarts.apache.org/zh/index.html",
      target: "self",
    },
    tooltip: {},
    series: [
      {
        type: "graph", // 图的类型
        layout: "force", // 图的布局 force | none | circular | tree | radial
        force: { // 力引导布局
          repulsion: 100, // 节点之间的斥力因子
          // edgeLength: 100, // 边的长度
        },
        edgeSymbol: ["circle", "arrow"], // 边的形状
        edgeSymbolSize: [4, 10], // 边的大小
        label: {
          show: true,
          position: "top",
        },
        // 数据
        data: [
          {
            name: "父亲",
            x: 300, // x 轴坐标
            y: 300, // y 轴坐标
            symbolSize: 50, // 节点大小
            itemStyle: { // 节点样式
              color: "red",
            },
          },
          {
            name: "母亲",
            x: 400,
            y: 300,
            symbolSize: 50,
            itemStyle: {
              color: "blue",
            },
          },
          {
            name: "儿子",
            x: 300,
            y: 200,
            symbolSize: 50,
            itemStyle: {
              color: "green",
            },
          },
          {
            name: "女儿",
            x: 400,
            y: 200,
            symbolSize: 50,
            itemStyle: {
              color: "yellow",
            },
          },
        ],
        // 关联关系
        links: [
          {
            source: "父亲", // 关联的起点
            target: "儿子", // 关联的终点
            relation: {
              name : "父子", // 关联的关系
              id: "1", // 关联的关系
            }, // 关联的关系
          },
          {
            source: "母亲",
            target: "儿子",
          },
          {
            source: "父亲",
            target: "女儿",
          },
          {
            source: "母亲",
            target: "女儿",
          },
        ],
      },
    ],
  });
});
</script>

<template>
  <div ref="myChart" id="relation" style="width: 600px; height: 400px"></div>
</template>