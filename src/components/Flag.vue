<template>
      <ul>
        <li style="float: left;" v-for="(obj, index) in numFlagArr" :key="index">
            <span :class="obj.colorStr">{{ index + 1 }}: {{ obj.selected }}</span>
        </li>
      </ul>
</template>
  
<script>
import eventBus from '../EventBus';
export default {
   props: ['numFlagArr'],
   created() {
        eventBus.$on('send', (selected, index) => {
            if (selected == '正确') {
                this.numFlagArr[index].colorStr = 'right';
            } else if (selected == '错误') {
                this.numFlagArr[index].colorStr = 'error';
            }
            this.numFlagArr[index].selected = selected;
        });
    },

};
</script>
  
<style scoped>
.right {
    color: green;
}

.error {
    color: red;
}

.undo {
    color: #ccc;
}

ul {
    list-style: none;
}

ul li {
    margin-left: 10px;
}
</style>