<template>
<div>
    <v-chart :options="chartData">
    </v-chart>
</div>
</template>

<script>
export default {
    data() {
        return {
            chartData: {
                xAxis: {
                    type: 'category'
                },
                yAxis: {},
                series: [{
                    type: 'line',
                    data: [100, 200, 300]
                }]
            }

        }
    }
}
</script>

<style>

</style>
