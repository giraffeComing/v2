<template>
  <div class="hold">
    <div class="item" v-for="(item,index) in insData.hold">
      <div class="title">
        <span class="lab blue">{{item.lab}}</span>
        <span class="name">{{item.name}}</span>
        <span class="price">{{item.price}}</span>
      </div>
      <div class="info">
        <span class="time">保单到期时间：{{item.endtime}}</span>
        <span class="name">保额</span>
      </div>
    </div>
    <!--暂无持仓-->
    <v-empty v-if="insData.hold.length<1" :opts="emptyData"></v-empty>
  </div>
</template>

<script>
  import VEmpty from '../../../components/common/empty/empty.vue'
  export default {
    name: '',
    components: {
      VEmpty
    },
    props: {
      insData: ""
    },
    methods:{
    },
    data () {
      return {
        emptyData: {
          icon:'type1',
          desc : '暂无记录'
        }
      }
    },
    created(){
    }
  }
</script>

<style scoped lang="scss" rel="stylesheet/scss">
  .hold{
    .item{
      display: block;
      padding:0 .6rem .3rem .24rem;
      border-bottom: 1px solid #f3f3f3;
      
      .title{
        position: relative;
        display: block;
        line-height: .9rem;
        color: #333;
        font-size: .32rem;
        padding-left: .68rem;
        @include clearfix;
  
        .lab{
          display: inline-block;
          height: .32rem;
          padding:0 .05rem;
          border-radius: 3px;
          text-align: center;
          line-height: .32rem;
          color: #fff;
          font-size: .22rem;
          position: absolute;
          left: 0;
          top: .29rem;
          background-color: #aeaeae;
    
          &.red{
            background-color: #ff484a;
          }
          &.orange{
            background-color: #ff8448;
          }
          &.blue{
            background-color: #4d98ff;
          }
          &.yellow{
            background-color: #fdb330;
          }
          &.grey{
            background-color: #aeaeae;
          }
        }
        
        .price{
          float: right;
        }
      }
      .info{
        padding-left: .68rem;
        color: #a0a0a0;
        font-size: .24rem;
        @include clearfix;
        
        .name{
          float: right;
        }
      }
    }
  }
</style>
