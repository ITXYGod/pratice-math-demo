<template>
  <div id="app">
    <h2>测试题</h2>
    <subject :numArr="arr"></subject>
    <div>
      <flag :numFlagArr="arr"></flag>
    </div>
  </div>
</template>

<script>
import subject from './components/Subject.vue';
import flag from './components/Flag.vue';
export default {
  data() {
    return {
        arr: [
          {
            num1: Math.floor(Math.random()*20),
            num2: Math.floor(Math.random()*20),
            selected: '未完成',
            colorStr: 'undo'
          },
          {
            num1: Math.floor(Math.random()*20),
            num2: Math.floor(Math.random()*20),
            selected: '未完成',
            colorStr: 'undo'
          },
          {
            num1: Math.floor(Math.random()*20),
            num2: Math.floor(Math.random()*20),
            selected: '未完成',
            colorStr: 'undo'
          },
          {
            num1: Math.floor(Math.random()*20),
            num2: Math.floor(Math.random()*20),
            selected: '未完成',
            colorStr: 'undo'
          },
          {
            num1: Math.floor(Math.random()*20),
            num2: Math.floor(Math.random()*20),
            selected: '未完成',
            colorStr: 'undo'
          },
        ]
    }
  },
  components: {
    subject,
    flag
  }
};
</script>

<style>
body {
  background-color: #eee;
}

#app {
  background-color: #fff;
  width: 500px;
  margin: 50px auto;
  box-shadow: 3px 3px 3px rgba(0, 0, 0, 0.5);
  padding: 2em;
}
</style>