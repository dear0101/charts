<template>
<common-card title="累计用户数" value="108,682,900">
    <template>
        <v-chart :options="getTotalUsers()"></v-chart>
    </template>
    <template v-slot:footer>
        <div class="compare-wrapper">
            <div class="total-users-footer">
                <span>日同比</span>
                <span class="emphasis">7.33%</span>
                <div class="increase"></div>
                <span class="mouth">月同比</span>
                <span class="emphasis">34.33%</span>
                <div class="decrease"></div>
            </div>
        </div>
    </template>
</common-card>
</template>

<script>
import commonCardMinxin from '../../mixins/commonCardMixin'

export default {
    mixins: [commonCardMinxin],
    data() {
        return {
            totalDatas: [130], //控制该数量的占比
            total: [430] //控制总数量
        }
    },
    methods: {
        getTotalUsers() {
            return {
                grid: {
                    top: 0,
                    left: 0,
                    right: 0,
                    bottom: 0
                },
                xAxis: {
                    type: 'value',
                    show: false
                },
                yAxis: {
                    type: 'category',
                    show: false
                },
                series: [{
                        type: 'bar',
                        data: this.totalDatas,
                        barWidth: 10,
                        stack: '总量',
                        itemStyle: {
                            color: '#45c946'
                        }
                    },
                    {
                        type: 'bar',
                        data: this.total,
                        stack: '总量',
                        itemStyle: {
                            color: '#eee'
                        }
                    },
                    {
                        type: 'custom',
                        stack: '总量',
                        data: this.totalDatas,
                        //自定义绘图
                        renderItem: (params, api) => {
                            //拿到data中的数据
                            const value = api.value(0)
                            //拿到坐标
                            const endPoint = api.coord([value, 0])
                            return {
                                type: 'group',
                                position: endPoint,
                                children: [{
                                        type: 'path',
                                        shape: {
                                            d: `M163.396608 289.168384c-40.577024 0-66.526208 
                                54.183936-35.44064 85.25824L477.217792 723.704832c20.031488 20.031488 
                                49.82272 20.031488 69.853184 0l349.274112-349.278208c30.30528-30.294016 
                                6.677504-85.25824-34.927616-85.25824L163.396608 289.168384z`,
                                            x: -5,
                                            y: -20,
                                            width: 10,
                                            height: 10,
                                            layout: 'cover', //填充
                                        },
                                        style: {
                                            fill: '#45c946'
                                        }
                                    },
                                    {
                                        type: 'path',
                                        shape: {
                                            d: `M131.974144 648.752128c-30.418944 30.430208-6.474752 
                                        84.301824 34.917376 84.301824L858.258432 733.053952c42.899456 0 
                                        65.325056-53.85216 34.916352-84.301824L547.487744 
                                        302.569472c-19.930112-19.974144-49.374208-19.95264-69.327872 
                                        0L131.974144 648.752128z`,
                                            x: -5,
                                            y: 10,
                                            width: 10,
                                            height: 10,
                                            layout: 'cover',
                                        },
                                        style: {
                                            fill: '#45c946'
                                        }
                                    }
                                ],
                            }
                        }
                    }
                ],
            }
        }
    },
}
</script>

<style lang="scss" scoped>
.total-users-footer {
    display: flex;
    align-items: center;

    .mouth {
        margin-left: 10px;
    }
}
</style>
