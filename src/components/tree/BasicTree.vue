<!-- 树图 -->
<script setup>
import * as echarts from "echarts";
import { onMounted, ref } from "vue";
const myChart = ref(null);

onMounted(() => {
  const myEcharts = echarts.init(myChart.value);
  // 树图
  myEcharts.setOption({
    title: {
      text: "ECharts 入门示例",
      link: "https://echarts.apache.org/zh/index.html",
      target: "self",
      subtext: "树图",
    },
    tooltip: {
      trigger: "item",
      triggerOn: "mousemove",
    },
    series: [
      {
        type: "tree",
        data: [
          {
            // 根节点
            name: "flare",
            // 子节点
            children: [
              {
                // 子节点
                name: "analytics",
                // 子节点
                children: [
                  {
                    name: "cluster",
                    children: [
                      { name: "AgglomerativeCluster", value: 3938 },
                      { name: "CommunityStructure", value: 3812 },
                      { name: "HierarchicalCluster", value: 6714 },
                      { name: "MergeEdge", value: 743 },
                    ],
                  },
                  {
                    name: "graph",
                    children: [
                      { name: "BetweennessCentrality", value: 3534 },
                      { name: "LinkDistance", value: 5731 },
                      { name: "MaxFlowMinCut", value: 7840 },
                      { name: "ShortestPaths", value: 5914 },
                      { name: "SpanningTree", value: 3416 },
                    ],
                  },
                  {
                    name: "optimization",
                    children: [{ name: "AspectRatioBanker", value: 7074 }],
                  },
                ],
              },
              {
                name: "animate",
                children: [
                  { name: "Easing", value: 17010 },
                  { name: "FunctionSequence", value: 5842 },
                  {
                    name: "interpolate",
                    children: [
                      { name: "ArrayInterpolator", value: 1983 },
                      { name: "ColorInterpolator", value: 2047 },
                      { name: "DateInterpolator", value: 1375 },
                      { name: "Interpolator", value: 8746 },
                      { name: "MatrixInterpolator", value: 2202 },
                      { name: "NumberInterpolator", value: 1382 },
                      { name: "ObjectInterpolator", value: 1629 },
                      { name: "PointInterpolator", value: 1675 },
                      { name: "RectangleInterpolator", value: 2042 },
                    ],
                  },
                  { name: "ISchedulable", value: 1041 },
                  { name: "Parallel", value: 5176 },
                  { name: "Pause", value: 449 },
                  { name: "Scheduler", value: 5593 },
                  { name: "Sequence", value: 5534 },
                  { name: "Transition", value: 9201 },
                  { name: "Transitioner", value: 19975 },
                  { name: "TransitionEvent", value: 1116 },
                  { name: "Tween", value: 6006 },
                ],
              },
            ],
          },
        ],
        // 树图的布局
        leaves: {
          // 叶子节点的布局
          label: {
            show: true, // 显示标签
            position: "right", // 标签的位置
            rotate: 0, // 标签的旋转角度
            color: "#000", // 标签的颜色
            fontStyle: "normal", // 标签的字体风格
            fontWeight: "normal",  // 标签的字体粗细
            fontFamily: "sans-serif", // 标签的字体
            fontSize: 12,
          },
          // 叶子节点的样式
          emphasis: {
            label: {
              show: true,
            },
          },
        },
      },
    ],
  });
});
</script>

<template>
  <div ref="myChart" id="tree1" style="width: 100%; height: 600px"></div>
</template>