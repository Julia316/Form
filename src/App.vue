
<template>

  <div id="app">
    <form-comp :list="list" @reduceCountHandle="reduceCount" @addCountHandle="addCount"> </form-comp>
    <div v-if="!list.length">购物车为空</div>
  </div>
</template>

<script>

import FormComp from './components/formcomp.vue'
export default{
  name: 'App',
  components: {
    FormComp
  },
  data: function () {
    return {
      list: [
        {
          id: 1,
          name: 'iPhone7',
          price: 6188,
          count: 1
        },
        {
          id: 2,
          name: 'iPad Pro',
          price: 5888,
          count: 1
        },
        {
          id: 3,
          name: 'MacBook Pro',
          price: 21488,
          count: 1
        }
      ]
    }
  },
  methods: {
    addCount: function (index) {
      this.list[index].count++
    },
    reduceCount: function (index) {
      this.list[index].count--
    }
  }
}

</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
