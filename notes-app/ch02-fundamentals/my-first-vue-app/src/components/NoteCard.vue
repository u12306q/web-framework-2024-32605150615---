<template>
  <div class="card">
    <h3>{{ title }}</h3>
    <p class="desc">这是一个单文件组件</p>

    <div class="info-row">
      <div class="info-item">
        <p>{{ message }}</p>
      </div>
      <div class="info-item">
        <p>{{ message.toUpperCase() }}</p>
      </div>
      <div class="info-item">
        <p>{{ 1 + 2 * 3 }}</p>
      </div>
    </div>

    <p class="count-box">count = {{ count }}（3 秒后自动变 100）</p>

    <img :src="imgSrc" width="80" />
    <p :class="{ active: count > 0 }">count 大于 0 时变绿色加粗</p>

    <div class="btn-row">
      <button @click="count++">count +1</button>
      <button @click="say('你好', $event)">say 方法</button>
    </div>

    <div class="form-box">
      <p>姓名：{{ form.name }} | 性别：{{ form.gender }} | 爱好：{{ form.hobby.join('、') }}</p>
      <input v-model="form.name" placeholder="输入姓名" />
      <label><input type="radio" value="男" v-model="form.gender" /> 男</label>
      <label><input type="radio" value="女" v-model="form.gender" /> 女</label>
      <label><input type="checkbox" value="打球" v-model="form.hobby" /> 打球</label>
      <label><input type="checkbox" value="编程" v-model="form.hobby" /> 编程</label>
    </div>

    <button class="toggle-btn" @click="show = !show">切换显隐</button>
    <p v-if="show" class="tip green">v-if：条件为真才显示</p>
    <p v-show="show" class="tip blue">v-show：只是隐藏元素</p>

    <ul class="list">
      <li v-for="(item, index) in subjects" :key="index">
        {{ index }} - {{ item }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'NoteCard',
  data() {
    return {
      title: '组件演示卡片',
      message: 'hello vue',
      count: 0,
      imgSrc: 'https://vuejs.org/images/logo.png',
      show: true,
      subjects: ['语文', '数学', 'Vue'],
      form: {
        name: '',
        gender: '',
        hobby: []
      }
    }
  },
  methods: {
    say(word, event) {
      alert(word + '｜事件类型：' + event.type)
    }
  },
  mounted() {
    setTimeout(() => {
      this.count = 100
    }, 3000)
  }
}
</script>

<style scoped>
.card {
  background: #ffffff;
  border: 2px solid #a5b4fc;
  border-radius: 14px;
  padding: 18px;
  margin-bottom: 20px;
  box-shadow: 0 4px 14px rgba(165, 180, 252, 0.25);
}

h3 {
  margin: 0 0 8px;
  color: #4f46e5;
}

.desc {
  color: #666;
}

.info-row {
  display: flex;
  gap: 10px;
  margin: 14px 0;
}

.info-item {
  flex: 1;
  background: #eef2ff;
  padding: 10px;
  border-radius: 10px;
  text-align: center;
}

.count-box {
  background: #fef3c7;
  padding: 10px;
  border-radius: 8px;
}

.active {
  color: #16a34a;
  font-weight: bold;
}

.btn-row {
  display: flex;
  gap: 10px;
  margin: 14px 0;
}

button {
  background: #4f46e5;
  color: #fff;
  border: none;
  padding: 10px 16px;
  border-radius: 8px;
  cursor: pointer;
}

button:hover {
  background: #4338ca;
}

.form-box {
  background: #f0fdf4;
  padding: 14px;
  border-radius: 10px;
  margin: 14px 0;
}

.form-box input {
  padding: 8px;
  border-radius: 8px;
  border: 1px solid #bbf7d0;
}

.toggle-btn {
  background: #f59e0b;
}

.tip {
  padding: 10px;
  border-radius: 8px;
}

.tip.green {
  background: #d1fae5;
  color: #065f46;
}

.tip.blue {
  background: #dbeafe;
  color: #1e40af;
}

.list {
  background: #f9fafb;
  padding: 14px;
  border-radius: 10px;
}

.list li {
  padding: 6px 0;
  border-bottom: 1px dashed #e5e7eb;
}
</style>
