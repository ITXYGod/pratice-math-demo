<template>
    <div class="subject">
        <ul>
            <li v-for="(obj, index) in numArr" :key="index">
                <span>{{ obj.num1 }}</span>
                <span>+</span>
                <span>{{ obj.num2 }}</span>
                <span>=</span>
                <input type="number" v-model="calcuVal"  value="index"/>
                <button @click="btn(index)">提交</button>
            </li>
        </ul>

    </div>
</template>
  
<script>
import eventBus from '../EventBus';
export default {
    data() {
        return {
            selected: '未完成',
            total: 0,
        }
    },
    props: ['numArr'],
    methods: {
        btn(index) {
          let temp = this.numArr[index].num1 + this.numArr[index].num2;
          if (this.total == temp) {
             this.selected = "正确";
             eventBus.$emit('send', this.selected, index);
             return;
          }
          this.selected = '错误';
          eventBus.$emit('send', this.selected, index);
        }
    },
    computed: {
        calcuVal: {
            set(val) {
              this.total = val;
            },
            get() {
             
            }
        }
    },
};
</script>
  
<style scoped>
.subject {
    margin: 5px;
    padding: 5px;
    font-size: 20px;
}

.subject span {
    display: inline-block;
    text-align: center;
    width: 20px;
}

.subject input {
    width: 50px;
    height: 20px;
}

ul {
    list-style: none;
}
</style>