<template>
<div>
    <ve-line :data='vchartData'>
    </ve-line>
</div>
</template>

<script>
export default {
    data() {
        return {
            vchartData: {
                columns: ['日期', '销售额'],
                rows: [{
                        '日期': '1月1号',
                        '销售额': 123
                    },
                    {
                        '日期': '1月2号',
                        '销售额': 123
                    }, {
                        '日期': '1月3号',
                        '销售额': 123
                    }, {
                        '日期': '1月4号',
                        '销售额': 123
                    }
                ]
            }
        }
    },
}
</script>

<style>

</style>
