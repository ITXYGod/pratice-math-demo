<template>
  <div>
    <Food :arr="list" @addApp="addCountFun" :totals="totalPrice" @subApp="subCountFun"></Food>
  </div>
</template>

<script>
import Food from './components/Food.vue';
export default {
  data() {
    return {
      list: [
        {
          "shopName": "可比克薯片",
          "price": 5.5,
          "count": 0
        },
        {
          "shopName": "草莓酱",
          "price": 3.5,
          "count": 0
        },
        {
          "shopName": "红烧肉",
          "price": 55,
          "count": 0
        },
        {
          "shopName": "方便面",
          "price": 12,
          "count": 0
        }
      ]
    }
  },
  components: {
    Food
  },
  methods: {
    addCountFun(index) {
      this.list[index].count++;
    },
    subCountFun(index) {
      this.list[index].count > 0 && this.list[index].count--;
    }
  },
  computed: {
    totalPrice() {
      return this.list.reduce((sum, obj) =>
        sum += obj.count * obj.price
        , 0);
    }
  }
}
</script>

<style lang="scss" scoped></style>