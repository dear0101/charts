<template>
<div class="top-view">
    <el-row :gutter="20">
        <el-col :span="6">
            <el-card shadow="hover">
                <total-sales />
            </el-card>
        </el-col>
        <el-col :span="6">
            <el-card shadow="hover">
                <total-orders />
            </el-card>
        </el-col>
        <el-col :span="6">
            <el-card shadow="hover">
                <today-users />
            </el-card>
        </el-col>
        <el-col :span="6">
            <el-card shadow="hover">
                <total-users />
            </el-card>
        </el-col>
    </el-row>
</div>
</template>

<script>
import TotalSales from '../TotalSates/index'
import TotalOrders from '../TotalOrders/index'
import TodayUsers from '../TodayUsers/index'
import TotalUsers from '../TotalUsers/index'
export default {
    name: 'TopView',
    components: {
        TotalSales,
        TotalOrders,
        TodayUsers,
        TotalUsers
    }
}
</script>

<style>

</style>
