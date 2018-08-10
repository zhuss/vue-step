<template>
    <div class="in-step-item" v-show="index == active">
        <slot></slot>
    </div>
</template>
<script>
export default {
    props:{
        title:String
    },
    data(){
        return {
            index:0,
            active:0
        }
    }
}
</script>

<style lang="less" scoped>
.in-step-item{
   padding: 30px 0;
}
</style>

