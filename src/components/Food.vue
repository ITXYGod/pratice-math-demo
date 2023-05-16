<template>
    <div>
       <h3>商品清单如下：</h3>
       <ul>
        <li v-for="(obj, index) in arr" :key="index">
            <span>{{ obj.shopName }}</span> {{ obj.price }} /份
        </li>
       </ul>
       <hr>
       <ul>
        <li v-for="(obj, index) in arr" :key="index">
           <span>{{ obj.shopName }}</span>  &nbsp;
            <button @click="addCount(index)">+</button>  &nbsp;
            <span>{{ obj.count }}</span>  &nbsp;
            <button @click="subCount(index)">-</button>
        </li>
       </ul>
       <hr>
       <p>总价为： {{ totals }}</p>
    </div>
</template>

<script>
    export default {
        props: ['arr', 'totals'],
        methods: {
            addCount(index) {
                this.$emit('addApp', index);
            },
            subCount(index) {
                this.$emit('subApp', index);
            }
        }
    }

</script>

<style scoped>
 li {
    list-style: none;
 }
</style>