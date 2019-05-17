<template>
    <div style="flex:1">
        <myPending></myPending>
    </div>
</template>

<!--引入bui-weex样式文件-->
<style lang="scss" src="bui-weex/src/css/buiweex.scss"></style>

<script>
    import myPending from "./myPending.vue";
    module.exports = {
        data () {
            return {}
        },
        components: {
          myPending
        }
    }
</script>