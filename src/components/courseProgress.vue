<template>
    <div class="container">
        <div ref="chart" class="chart"></div>
    </div>
</template>
  
<script>
import * as echarts from 'echarts';

export default {
    mounted() {
        this.drawChart();
    },
    methods: {
        drawChart() {
            const chartElement = this.$refs.chart;
            const chart = echarts.init(chartElement);

            // 模拟数据
            const courses = [
                { name: '课程1', progress: 60 },
                { name: '课程2', progress: 80 },
                { name: '课程3', progress: 40 },
                { name: '课程4', progress: 75 },
                { name: '课程5', progress: 90 },
                { name: '课程6', progress: 55 },
            ];

            // 配置项
const option = {
    tooltip: {
        trigger: 'axis',
        axisPointer: {
            type: 'shadow',
        },
    },
    grid: {
        left: '3%',
        right: '4%',
        bottom: '3%',
        containLabel: true,
    },
    xAxis: {
        type: 'value',
        max: 100,
        axisLabel: {
            formatter: '{value}%',
        },
    },
    yAxis: {
        type: 'category',
        data: courses.map(course => course.name),
        name: '课程名称',
    },
    series: [
        {
            name: '进度',
            type: 'bar',
            data: courses.map(course => course.progress),
            itemStyle: {
                color: '#87cefa',
            },
            label: {
                show: true,
                position: 'inside',
                formatter: '{c}%',
            },
        },
    ],
};

// 初始化图表并设置配置项
chart.setOption(option);
        },
    },
};
</script>
  
<style>
.chart {
    width: 800px;
    height: 300px;
}
</style>
  