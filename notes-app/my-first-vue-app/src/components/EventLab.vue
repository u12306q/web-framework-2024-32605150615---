<template>
  <div class="event-lab">
    <h3>🎯事件实验室‑冒泡演示</h3>
    <div class="bubble" @click="log('outer 触发（外层 @click）')">
      <button @click.stop="log('inner 触发（.stop：冒泡被阻止）')">内层 .stop</button>
      <button @click="log('inner 触发（无 .stop：冒泡到外层）')">内层 无.stop</button>
    </div>
    <ol class="logs">
      <li v-for="(item, index) in logs" :key="index">{{ item }}</li>
    </ol>
  </div>
</template>

<script>
export default {
  name:'EventLab',
  data(){
    return {
      logs:[]
    }
  },
  methods:{
    log(msg){
      this.logs.unshift(msg)
      console.log(msg)
    }
  }
}
</script>

<style scoped>
.event-lab {
  border:1px dashed #b8860b;
  padding:12px 16px;
  border-radius:8px;
  margin-top:20px;
}
.bubble {
  border: 2px solid #42b883;
  padding: 6px 10px;
  margin: 6px 0;
}
.logs {
  background:#fafafa;
  border-left:3px solid #b8860b;
  padding:4px 8px 4px 28px;
  min-height:2em;
}
</style>
