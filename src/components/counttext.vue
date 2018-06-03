<template>
  <div class="counttext">
    <span class="reduce" @click="reduceHandle">-</span>
    <span class="num">{{count}}</span>
    <span class="add" @click="addHandle">+</span>
  </div>
</template>

<script>
export default {
  props: {
    count: {
      type: Number
    }
  },
  methods: {
    reduceHandle: function () {
      this.$emit('reduce')
    },
    addHandle: function () {
      this.$emit('add')
    }
  }

}
</script>

<style lang="less">
  @import '../common/less/mixin.less';
  .counttext{
    @textAlign();
    font-size:0;
    .reduce,.add{
      display:inline-block;
      vertical-align: middle;
      @textAlign();
      color:#ccc;
      font-size:16px;
      width:20px;
      height:20px;
      border:1px solid #ddd;
      border-radius:50%;
      cursor:pointer;

    }
    .num{
      display:inline-block;
      width:30px;
      font-size:20px;
      color:blue;
      line-height:50px;
      vertical-align: middle;
    }
  }
</style>
