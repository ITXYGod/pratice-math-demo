<template>
  <div>
    <Cart :arr="goodList" 
    @addCountApp="addCountFun"
    @subCountApp="subCountFun"
    @deleteDataApp="deleteDataFun"
    ></Cart>
  </div>
</template>

<script>
import Cart from './components/ShoppingCart.vue';
  export default {
    data() {
      return {
        goodList: [
          {
            name: "诸葛亮",
            price: 1000,
            num: 1,
            checked: false,
          },
          {
            name: "蔡文姬",
            price: 1500,
            num: 1,
            checked: false,
          },
          {
            name: "妲己",
            price: 2000,
            num: 1,
            checked: false,
          },
          {
            name: "鲁班",
            price: 2200,
            num: 1,
            checked: false,
          },
        ],
      };
    },
    components: {
       Cart
    },
    methods: {
      addCountFun(index) {
        this.goodList[index].num++;
      },
      subCountFun(index) {
        this.goodList[index].num > 1 && this.goodList[index].num--;
      },
      deleteDataFun(index) {
        this.goodList.splice(index, 1);
      }
    }
  }
</script>

<style lang="scss" scoped>

</style>