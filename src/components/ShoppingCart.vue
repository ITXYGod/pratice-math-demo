<template>
    <div>
      <table
        border="1"
        width="700"
        style="border-collapse: collapse"
      >
        <caption>
          购物车
        </caption>
        <thead>
          <tr>
            <th>
              <input type="checkbox" v-model="isAll"/> <span>全选</span>
            </th>
            <th>名称</th>
            <th>价格</th>
            <th>数量</th>
            <th>总价</th>
            <th>操作</th>
          </tr>
        </thead>
        <tbody>
           <tr v-for="(obj, index) in arr" :key="index">
            <td><input type="checkbox" v-model="obj.checked"></td>
            <td>{{ obj.name }}</td>
            <td>{{ obj.price }}</td>
            <td>
               <button @click="subCountFun(index)">-</button>&nbsp;
               <span>{{ obj.num }}</span>&nbsp;
               <button @click="addCountFun(index)">+</button>
            </td>
            <td>{{ obj.price * obj.num }}</td>
            <td>
                <button @click="deleteFun(index)">删除</button>
            </td>
           </tr>
        </tbody>
        <tfoot>
          <tr>
            <td>合计:</td>
            <td colspan="5">
               {{ total}}
            </td>
          </tr>
        </tfoot>
      </table>
    </div>
  </template>
  
  <script>
  export default {
     props: ['arr'],
     methods: {
        addCountFun(index) {
            this.$emit('addCountApp', index);
        },
        subCountFun(index) {
            this.$emit('subCountApp', index);
        },
        deleteFun(index) {
            this.$emit('deleteDataApp', index);
        }
     },
     computed: {
        isAll: {
            set(selected) {
                this.arr.forEach(obj => obj.checked = selected);
            },
            get() {
                return this.arr.every(obj => obj.checked === true)
            }
        },
        total: {
            get() {
              return this.arr.filter(obj => obj.checked === true).reduce((sum, obj) => sum += obj.price  * obj.num, 0)
            }
        }
     }
  };
  </script>
  
  <style>
  </style>