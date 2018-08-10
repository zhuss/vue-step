<template>
    <div class="view-demo">
        <step-wrap :active="active">
            <step-item title="第一步">
                <div class="content">
                    <h2>Vue.js 是什么</h2>
                    <p>Vue (读音 /vjuː/，类似于 view) 是一套用于构建用户界面的渐进式框架。与其它大型框架不同的是，Vue 被设计为可以自底向上逐层应用。Vue 的核心库只关注视图层，不仅易于上手，还便于与第三方库或既有项目整合。另一方面，当与现代化的工具链以及各种支持类库结合使用时，Vue 也完全能够为复杂的单页应用提供驱动。</p>
                    <p>如果你想在深入学习 Vue 之前对它有更多了解，我们制作了一个视频，带您了解其核心概念和一个示例工程。</p>
                    <p>如果你已经是有经验的前端开发者，想知道 Vue 与其它库/框架有哪些区别，请查看对比其它框架。</p>
                </div>
            </step-item>
            <step-item title="第二步">
                <div class="content">
                    <h2>起步</h2>
                    <p>尝试 Vue.js 最简单的方法是使用 JSFiddle 上的 Hello World 例子。你可以在浏览器新标签页中打开它，跟着例子学习一些基础用法。或者你也可以创建一个 .html 文件，然后通过如下方式引入 Vue：</p>
                    <p>安装教程给出了更多安装 Vue 的方式。请注意我们不推荐新手直接使用 vue-cli，尤其是在你还不熟悉基于 Node.js 的构建工具时。</p>
                    <p>如果你喜欢交互式的东西，你也可以查阅这个 Scrimba 上的系列教程，它揉合了录屏和代码试验田，并允许你随时暂停和播放。</p>
                </div>
            </step-item>
            <step-item title="第三步">
                <div class="content">
                    <h2>声明式渲染</h2>
                    <p>Vue.js 的核心是一个允许采用简洁的模板语法来声明式地将数据渲染进 DOM 的系统：</p>
                    <p>我们已经成功创建了第一个 Vue 应用！看起来这跟渲染一个字符串模板非常类似，但是 Vue 在背后做了大量工作。现在数据和 DOM 已经被建立了关联，所有东西都是响应式的。我们要怎么确认呢？打开你的浏览器的 JavaScript 控制台 (就在这个页面打开)，并修改 app.message 的值，你将看到上例相应地更新。</p>
                    <p>除了文本插值，我们还可以像这样来绑定元素特性：</p>
                </div>
            </step-item>
            <step-item title="第四步">
                <div class="content">
                    <h2>条件与循环</h2>
                    <p>控制切换一个元素是否显示也相当简单：</p>
                    <p>继续在控制台输入 app3.seen = false，你会发现之前显示的消息消失了。</p>
                    <p>这个例子演示了我们不仅可以把数据绑定到 DOM 文本或特性，还可以绑定到 DOM 结构。此外，Vue 也提供一个强大的过渡效果系统，可以在 Vue 插入/更新/移除元素时自动应用过渡效果。</p>
                    <p>还有其它很多指令，每个都有特殊的功能。例如，v-for 指令可以绑定数组的数据来渲染一个项目列表：</p>
                    <p>在控制台里，输入 app4.todos.push({ text: '新项目' })，你会发现列表最后添加了一个新项目。</p>
                </div>
            </step-item>
        </step-wrap>
        <button class="button" @click="active--" v-show="active>0">上一步</button>
        <button class="button" @click="active++" v-show="active<3">下一步</button>
        <button class="button" @click="submitClick" v-show="active==3">完成</button>
    </div>
</template>
<script>
import StepWrap from '../components/step/StepWrap';
import StepItem from '../components/step/StepItem';
export default {
    components:{
        StepWrap,
        StepItem
    },
    data(){
        return {
            active:0
        }
    },
    methods:{
        submitClick(){
            console.log(this.active);
        }
    }
}
</script>
<style lang="less" scoped>
.view-demo{
    width: 600px;
    padding: 50px 0;
    margin: 0 auto;
    .content{
        >h2{
           font-size: 20px;
        }
        p{
            line-height: 26px;
            margin: 20px 0;
        }
    }
    .button{
        cursor: pointer;
        outline: none;
        min-width: 100px;
        padding: 0 20px;
        height: 40px;
        color: #42b983;
        border: 2px solid #42b983;
        box-sizing: border-box;
    }
}
</style>


