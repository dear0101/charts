<template>
<div class="sales-view">
    <el-card shadow="hover">
        <template v-slot:header>
            <div class="menu-wrapper">
                <el-menu class="sales-view-el-menu" mode="horizontal" :default-active="activeIndex" @select="onMenuSelect">
                    <el-menu-item index="1">销售额</el-menu-item>
                    <el-menu-item index="2">访问量</el-menu-item>
                </el-menu>
                <div class="menu-right">
                    <el-radio-group v-model="radioSelect" size="small">
                        <el-radio-button label="今日"></el-radio-button>
                        <el-radio-button label="明日"></el-radio-button>
                        <el-radio-button label="今年"></el-radio-button>
                        <el-radio-button label="明年"></el-radio-button>
                    </el-radio-group>
                    <el-date-picker class="data-picker" unlink-panels type="daterange" v-model="dateData" range-separator="至" start-placeholder="开始日期" end-placeholder="结束日期" size='small' :picker-options="pickerOptions"></el-date-picker>
                </div>
            </div>
        </template>
        <template>
            <div>222</div>
        </template>
    </el-card>
</div>
</template>

<script>
export default {
    data() {
        return {
            activeIndex: '1',
            radioSelect: '今日',
            dateData: null,
            pickerOptions: {
                shortcuts: [{
                        text: '最近一周',
                        onClick(picker) {
                            const start = new Date()
                            const end = new Date()
                            //往回算7天,改变start
                            start.setTime(start.getTime() - 3600 * 24 * 1000 * 7)
                            picker.$emit('pick', [start, end])
                        }
                    },
                    {
                        text: '最近一个月',
                        onClick(picker) {
                            const start = new Date()
                            const end = new Date()
                            //往回算7天,改变start
                            start.setTime(start.getTime() - 3600 * 24 * 1000 * 30)
                            picker.$emit('pick', [start, end])
                        }
                    },
                    {
                        text: '最近三个月',
                        onClick(picker) {
                            const start = new Date()
                            const end = new Date()
                            //往回算7天,改变start
                            start.setTime(start.getTime() - 3600 * 24 * 1000 * 90)
                            picker.$emit('pick', [start, end])
                        }
                    }
                ],
            }
        }
    },
    methods: {
        onMenuSelect(index) {
            this.activeIndex = index
        }
    }
}
</script>

<style lang="scss" scoped>
.menu-wrapper {
    display: flex;
    position: relative;

    .sales-view-el-menu {
        width: 100%;
        padding-left: 20px;

        .el-menu-item {
            height: 50px;
            line-height: 50px;
            margin: 0 20px;
        }
    }

    .menu-right {
        position: absolute;
        top: 0;
        right: 20px;
        height: 50px;
        display: flex;
        align-items: center;
        justify-content: flex-end;

        .data-picker {
            margin-left: 20px;
        }
    }
}
</style>
