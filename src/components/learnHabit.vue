<template>
    <div class="container">
        <div ref="heatmapChart" class="habit-chart"></div>
    </div>
</template>
  
<script>
import * as echarts from 'echarts';

export default {
    mounted() {
        this.renderHeatmapChart();
    },
    methods: {
        renderHeatmapChart() {
            const heatmapChart = echarts.init(this.$refs.heatmapChart);

            const heatmapData = [
                [0, 0, 5], [0, 1, 10], [0, 2, 15], [0, 3, 12], [0, 4, 8], // 示例数据，可以根据实际情况替换
                [1, 0, 8], [1, 1, 15], [1, 2, 20], [1, 3, 18], [1, 4, 10],
                [2, 0, 12], [2, 1, 18], [2, 2, 25], [2, 3, 22], [2, 4, 15],
                [3, 0, 10], [3, 1, 20], [3, 2, 18], [3, 3, 15], [3, 4, 10],
                [4, 0, 6], [4, 1, 12], [4, 2, 18], [4, 3, 16], [4, 4, 8],
            ];

const option = {
    tooltip: {
        position: 'top',
    },
    grid: {
        height: '50%',
        y: '10%',
    },
    xAxis: {
        type: 'category',
        data: ['周一', '周二', '周三', '周四', '周五'],
    },
    yAxis: {
        type: 'category',
        data: ['上午', '下午', '晚上', '深夜', '凌晨'],
    },
    visualMap: {
        min: 0,
        max: 30,
        calculable: true,
        orient: 'horizontal',
        left: 'center',
        bottom: '20%',
    },
    series: [{
        name: '学习活跃度',
        type: 'heatmap',
        data: heatmapData,
        label: {
            show: true,
        },
        emphasis: {
            itemStyle: {
                shadowBlur: 10,
                shadowColor: 'rgba(0, 0, 0, 0.5)',
            },
        },
    }],
};

heatmapChart.setOption(option);
        },
    },
};
</script>
  
<style>
.container {
    display: flex;
    justify-content: center;
}

.habit-chart {
    width: 800px;
    height: 400px;
    margin: 20px;
}
</style>
  