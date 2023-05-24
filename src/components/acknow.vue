<template>
    <div class="container">
      <div class="chart">
        <div ref="pieChart" class="chart-item"></div>
        <div ref="radarChart" class="chart-item"></div>
      </div>
    </div>
  </template>
  
  <script>
  import * as echarts from 'echarts';
  
  export default {
    mounted() {
      this.drawCharts();
    },
    methods: {
      drawCharts() {
        const pieChartElement = this.$refs.pieChart;
        const pieChart = echarts.init(pieChartElement);
  
        const radarChartElement = this.$refs.radarChart;
        const radarChart = echarts.init(radarChartElement);
  
        // 模拟数据
        const knowledgePoints = [
          { name: '知识点1', mastery: 80 },
          { name: '知识点2', mastery: 60 },
          { name: '知识点3', mastery: 90 },
          { name: '知识点4', mastery: 70 },
          { name: '知识点5', mastery: 50 },
        ];
  
// 饼图配置项
const pieOption = {
  tooltip: {
    trigger: 'item',
    formatter: '{b}: {d}%',
  },
  series: [
    {
      name: '知识点掌握情况',
      type: 'pie',
      radius: '60%',
      data: knowledgePoints.map(point => ({
        name: point.name,
        value: point.mastery,
      })),
      label: {
        formatter: '{b}: {d}%',
      },
    },
  ],
};

// 雷达图配置项
const radarOption = {
  tooltip: {},
  radar: {
    indicator: knowledgePoints.map(point => ({ name: point.name })),
  },
  series: [
    {
      name: '知识点掌握情况',
      type: 'radar',
      data: [
        {
          value: knowledgePoints.map(point => point.mastery),
        },
      ],
    },
  ],
};
  
        // 初始化图表并设置配置项
        pieChart.setOption(pieOption);
        radarChart.setOption(radarOption);
      },
    },
  };
  </script>
  
  <style>
  .chart {
    display: flex;
    justify-content: space-between;
    width: 800px;
  }
  
  .chart-item {
    width: 400px;
    height: 300px;
  }
  </style>
  