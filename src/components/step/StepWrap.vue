<template>
    <div class="in-step-wrap">
        <div class="in-step-head">
            <div class="in-step-index" :class="{'in-step-active':index<=currentActive}" v-for="(item,index) in titleArray">
                <p class="in-step-label">{{item}}</p>
                <p class="in-step-progress"></p>
            </div>
        </div>
        <div class="in-step-body">
            <slot></slot>
        </div>
    </div>
</template>
<script>
export default {
    props:{
        active:{
            type:Number
        }
    },
    data(){
        return {
            titleArray:[],
            currentActive:-1
        }
    },
    watch:{
        active(value){
            for(let i = 0; i < this.$children.length; i++){
                this.$children[i].active = value;
                this.currentActive = this.active;
            }
        }
    },
    mounted(){
        this.initData();
        setTimeout(()=>{
            this.currentActive = this.active;
        },1);
    },
    methods:{
        initData(){
            this.getTitleArray();
        },
        getTitleArray(){
            let titleArray = []
            for(let i = 0; i < this.$children.length; i++){
                titleArray.push(this.$children[i].title);
                this.$children[i].index = i;
            }
            this.titleArray = titleArray;
        }
    }
}
</script>
<style lang="less" scoped>
.in-step-wrap{
    width: 100%;
    height: auto;
    >.in-step-head{
        width: 100%;
        height: 40px;
        line-height: 36px;
        display: flex;
        border:2px solid #42b983;
        box-sizing: border-box;
        >.in-step-index{
            flex: 1;
            height: 100%;
            position: relative;
            >.in-step-label{
                position: absolute;
                width: 100%;
                height: 100%;
                text-align: center;
                font-size: 12px;
                color:#42b983;
                transition: color .5s ease-in-out;
            }
            >.in-step-progress{
                width: 0px;
                height: 100%;
                background: #42b983;
                transition: width .5s ease-in-out;
            }
        }
        >.in-step-active{
            >.in-step-label{
             color: #FFF;
            }
            >.in-step-progress{
                width: 100%;
            }
        }
    }
}
</style>

