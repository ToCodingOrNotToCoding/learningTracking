<template>
    <div class="container">
        <div class="chart-container">
            <div ref="chart" class="chart"></div>
        </div>
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
            const timeData = ['周一', '周二', '周三', '周四', '周五', '周六'];
            const studyTimeData = [
                { name: '用户A', values: [120, 200, 150, 80, 70, 90] },
                { name: '用户B', values: [80, 120, 100, 60, 50, 70] },
                { name: '用户C', values: [150, 180, 160, 120, 110, 130] }
            ];
            const resourceData = [
                { name: '用户A', values: [10, 5, 8, 3, 6, 7] },
                { name: '用户B', values: [7, 9, 5, 8, 4, 6] },
                { name: '用户C', values: [5, 6, 7, 9, 8, 4] }
            ];

// 配置选项
const options = {
    tooltip: {
        trigger: 'axis',
        axisPointer: {
            type: 'shadow'
        }
    },
    legend: {
        data: studyTimeData.map(item => item.name)
    },
    xAxis: {
        type: 'category',
        data: timeData
    },
    yAxis: [
        {
            type: 'value',
            name: '学习时间',
            position: 'left',
        },
        {
            type: 'value',
            name: '学习资源使用次数',
            position: 'right'
        }
    ],
    series: [
        ...studyTimeData.map((item) => ({
            name: item.name,
            type: 'bar',
            data: item.values,
            yAxisIndex: 0,
        })),
        ...resourceData.map((item) => ({
            name: item.name,
            type: 'line',
            data: item.values,
            yAxisIndex: 1,
        }))
    ]
};

// 绘制图表
chart.setOption(options);
        },
    }
};
</script>
<style scoped>

.chart-container {
    width: 800px;
    height: 400px;
}

.chart {
    width: 100%;
    height: 100%;
}
</style>
  