<template>
    <div>
        <div class="tabs">
            <div class="tab"
                 v-for="(item,index) in tabs"
                 :class="{current:idx===index}"
                 @click="changeTab(index,item.tabView)">
                {{item.tabContent}}
            </div>
        </div>
        <!--动态组件-->
        <div class="tab-contains">
            <!--过渡效果-->
            <transition mode="out-in" name="fadeIn">
                <keep-alive>
                    <component :is="currentView"></component>
                </keep-alive>
            </transition>
        </div>
    </div>
</template>

<script>
    import VTabChild01 from './child01'
    import VTabChild02 from './child02'
    export default {
        name: '',
        components: {
            VTabChild01,
            VTabChild02,
        },
        data () {
            return {
                tabs:[
                    {
                        tabContent:'持有中',
                        tabView:'VTabChild01'
                    },
                    {
                        tabContent:'交易记录',
                        tabView:'VTabChild02'
                    }
                    ],
                idx:0,
                currentView:'VTabChild01'
            }
        },
        methods:{
            changeTab:function (i,v) {
                this.idx=i;
                this.currentView=v
//                触发BS的刷新放在这里不太合适，应该放在child02里axios的成功回调里面触发，通过bus或者vuex来管理
                this.$emit('refresh')
            }
        }
    }
</script>

<style scoped lang="scss" rel="stylesheet/scss">
    .tabs{
        background: #fff;
        height: 1.1rem;
        border-bottom: 1px solid #f3f3f3;
        display: flex;
        .tab{
            flex: 1;
            line-height: 1.1rem;
            height: 1.1rem;
            text-align: center;
            color: #a0a0a0;
            float: left;
            transition: all .3s
        }
        .current{
            border-bottom: 2px solid #ef4352;
            color: #333;
        }
    }
    .tab-contains{
        .tab-contain{
            display: none;
        }
        .current{
            display: block;
        }
    }
    .fadeIn-enter-active, .fadeIn-leave-active {
        transition: opacity .3s,transform .2s;
    }
    .fadeIn-enter, .fadeIn-leave-to {
        opacity: 0;
        transform: translateY(.2rem);
    }
</style>
