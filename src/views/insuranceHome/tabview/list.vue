<template>
  <div class="list">
    <div class="item" v-for="(item,index) in insData.list" @click="toDetail(item)">
      <a href="javascript:;">
        <img :src="item.logo" alt="">
        <div class="title">{{item.name}}</div>
        <div class="txt">{{item.brief}}</div>
        <div class="price"><span>{{item.money}}</span>元起</div>
      </a>
    </div>
    <!--暂无持仓-->
    <v-empty v-if="insData.list.length<1" :opts="emptyData"></v-empty>
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
      insData: ''
    },
    methods:{
      toDetail(item) {
        this.$router.push({
            path:'/bxForm',
            query:{id:item.id}
        })
      }
    },
    data () {
      return {
        emptyData: {
          icon:'type1',
          desc : '暂无记录'
        }
      }
    }
  }
</script>

<style scoped lang="scss" rel="stylesheet/scss">
  .list{
    padding:0 .2rem;
    background-color: #fff;
    .item{
      position: relative;
      display: block;
      border-top: 1px dashed #eee;
      min-height: 2.4rem;
      &:first-child{
        border-top: 0;
      }
      & > a{
        display: block;
        padding:.2rem 0 .2rem 3.2rem;
      }
      
      img{
        position: absolute;
        left: 0;
        top:.2rem;
        width: 2.8rem;
        height: 2rem;
      }
      .title{
        color: #333;
        font-size: .4rem;
        margin-top: .2rem;
      }
      .txt{
        color: #666;
        font-size: .26rem;
        margin-top: .2rem;
      }
      .price{
        color: #999;
        font-size: .26rem;
        margin-top: .4rem;
        span{
          display: inline-block;
          vertical-align: text-bottom;
          font-size: .4rem;
          color: #f14d4c;
        }
      }
      
      
    }
  }
</style>
