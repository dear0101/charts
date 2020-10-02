<template>
<common-card title="累计订单量" value="2,521,900">
    <template>
        <div id="total-orders-chart" :style="{width:'100%',height:'100%'}"></div>
    </template>
    <template v-slot:footer>
        <span>昨日订单量</span>
        <span class="emphasis"> 2,000,000</span>
    </template>
</common-card>
</template>

<script>
import commonCardMinxin from '../../mixins/commonCardMixin'
export default {
    mixins: [commonCardMinxin],
    data() {
        return {
            ordersChartData: [639, 534, 200, 544, 600, 746, 430, 222, 420, 522, 320, 802, 420, 522, 320]
        }
    },
    mounted() {
        const chartDom = document.getElementById('total-orders-chart')
        const chart = this.$echarts.init(chartDom)
        chart.setOption({
            xAxis: {
                type: 'category',
                show: false,
                boundaryGap: false //x轴的左右间隙

            },
            yAxis: {
                show: false

            },
            series: [{
                type: 'line',
                data: this.ordersChartData,
                areaStyle: {
                    color: 'purple'
                },
                lineStyle: {
                    width: 0
                },
                itemStyle: {
                    opacity: 0
                },
                smooth: true //平滑效果
            }],
            //布局
            grid: {
                top: 0,
                left: 0,
                right: 0,
                bottom: 0
            }

        })
    }
}
</script>

<style scoped>

</style>
