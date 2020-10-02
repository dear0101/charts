<template>
<common-card title="今日交易用户数" value="9,900">
    <template>
        <v-chart :options="getTodayUsers()"></v-chart>
    </template>
    <template v-slot:footer>
        <span>退货率</span>
        <span class="emphasis"> 5.33%</span>
    </template>
</common-card>
</template>

<script>
import commonCardMinxin from '../../mixins/commonCardMixin'

export default {
    mixins: [commonCardMinxin],
    data() {
        return {
            userChartData: [639, 534, 200, 544, 600, 746, 430, 222, 420, 522, 320, 802, 420, 522],
            userXHoverData: ['00.00', '01.00', '02.00', '03.00', '04.00', '05.00', '06.00', '07.00', '08.00', '09.00', '10.00', '11.00', '12.00', '13.00']
        }
    },
    methods: {
        getTodayUsers() {
            return {
                color: ['#3398DB'],
                //x轴
                xAxis: {
                    type: 'category',
                    data: this.userXHoverData,
                    boundaryGap: false, //x轴的左右间隙
                    show: false
                },
                //y轴
                yAxis: {
                    show: false
                },
                //图
                series: [{
                    type: 'bar', //类型竖状图
                    barWidth: '60%', //每条的宽度
                    data: this.userChartData,
                }],
                //布局
                grid: {
                    top: 0,
                    left: 0,
                    right: 0,
                    bottom: 0
                }

            }
        }
    },
}
</script>

<style>

</style>
