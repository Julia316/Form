<template>
  <div class="form" v-if="list.length">
    <table cellpadding="0" cellspacing="0">
      <thead>
        <tr>
          <th></th>
          <th>商品名称</th>
          <th>商品单价</th>
          <th>购买数量</th>
          <th>操作</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="item in list" :key="item.id">
          <td>{{item.id}}</td>
          <td>{{item.name}}</td>
          <td>{{item.price}}</td>
          <td>
            <!--<count-text></count-text>-->
          </td>
          <td><input type="button" value="移除"></td>
        </tr>
      </tbody>
    </table>
    <div class="total_price">总价：￥{{total}}</div>
  </div>
</template>

<script>
import CountText from './counttext.vue'
export default{
  props: {
    list: {
      type: Array
    }
  },
  components: {
    CountText
  },
  data: function () {
    return {
      countNum: 1
    }
  },
  computed: {
    total: function () {
      let total = 0
      for (let i = 0; i < this.list.length; i++) {
        total += this.list[i].price * this.list[i].count
      }
      let arr = total.toLocaleString()
      console.log(arr)
      return arr
    }
  }
}
</script>

<style lang="less">
  @import "../common/less/mixin.less";
  .form{
    @widthL();
    @margin();
    @textAlign();
    table{
      @widthM();
      @margin();
      border-collapse:collapse;
      thead{
        color:#aaa !important;
        @colorBg();
        @border();
        tr{
          color:#000;
          height: 50px;
        }
      }
      tbody{
        color:#000;
        tr{
          height:@height50;
          td{
            @borderB();
            @borderR();
            &:first-of-type{
              @borderL();
              width:60px;
            }
          }
        }
      }
    }
    .total_price{
      @widthM();
      text-align:left;
      margin:5px auto 0;
    }
  }

</style>
