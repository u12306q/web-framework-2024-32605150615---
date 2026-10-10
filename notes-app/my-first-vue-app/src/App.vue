<template>
  <div class="page">
    <header class="title">
      <h1>江贤松的记事本</h1>
      <p>notes-app · 实验2</p>
    </header>

    <NoteCard />

    <section class="add-card">
      <h2>添加笔记</h2>
      <input
        v-model="newNote"
        placeholder="输入笔记内容，按回车添加"
        @keyup.enter="addNote"
      />
      <div class="options">
        <label><input type="radio" value="高" v-model="level" /> 高</label>
        <label><input type="radio" value="中" v-model="level" /> 中</label>
        <label><input type="radio" value="低" v-model="level" /> 低</label>
        <label><input type="checkbox" value="学习" v-model="tags" /> 学习</label>
        <label><input type="checkbox" value="生活" v-model="tags" /> 生活</label>
      </div>
      <p class="preview">
        预览：{{ newNote || '（空）' }} | {{ level }} | {{ tags.join('、') || '无标签' }}
      </p>
      <button class="add-btn" @click="addNote">添加笔记</button>
    </section>

    <section class="list-card">
      <h2>笔记列表</h2>
      <div
        v-for="(item, index) in noteList"
        :key="index"
        class="note-item"
        :class="item.level"
      >
        <div class="note-left">
          <span class="index">{{ index + 1 }}</span>
          <div>
            <p class="note-text">{{ item.content }}</p>
            <p class="note-meta">优先级：{{ item.level }} | 标签：{{ item.tags.join('/') || '无' }}</p>
          </div>
        </div>
        <button class="del-btn" @click="noteList.splice(index, 1)">删除</button>
      </div>
      <p v-if="noteList.length === 0" class="empty">还没有笔记，快来添加一条吧</p>
      <p v-show="noteList.length > 0" class="count">共 {{ noteList.length }} 条笔记</p>
    </section>

    <!-- 冒泡组件在这里！！ -->
    <hr>
    <EventLab />
  </div>
</template>

<script>
import EventLab from './components/EventLab.vue'
import NoteCard from './components/NoteCard.vue'

export default {
  components: { NoteCard, EventLab },
  data() {
    return {
      newNote: '',
      level: '中',
      tags: [],
      noteList: []
    }
  },
  methods: {
    addNote() {
      if (!this.newNote.trim()) return
      this.noteList.push({
        content: this.newNote.trim(),
        level: this.level,
        tags: [...this.tags]
      })
      this.newNote = ''
    }
  }
}
</script>

<style scoped>
.page {
  max-width: 640px;
  margin: 30px auto;
  padding: 0 20px;
}

.title {
  text-align: center;
  color: #4f46e5;
}

.title h1 {
  margin: 0;
  font-size: 26px;
}

.title p {
  margin: 4px 0 20px;
  color: #888;
}

.add-card,
.list-card {
  background: #ffffff;
  border-radius: 14px;
  padding: 18px;
  margin-bottom: 20px;
  box-shadow: 0 4px 14px rgba(79, 70, 229, 0.12);
}

h2 {
  margin-top: 0;
  color: #4f46e5;
  font-size: 18px;
}

input {
  width: 100%;
  box-sizing: border-box;
  padding: 12px 14px;
  border: 1px solid #e0e0e0;
  border-radius: 10px;
  font-size: 15px;
  outline: none;
}

input:focus {
  border-color: #4f46e5;
}

.options {
  margin: 14px 0;
  display: flex;
  gap: 10px;
  flex-wrap: wrap;
}

.options label {
  background: #f3f4f6;
  padding: 8px 12px;
  border-radius: 8px;
  font-size: 14px;
}

.preview {
  background: #eef2ff;
  color: #4f46e5;
  padding: 10px 12px;
  border-radius: 8px;
  font-size: 14px;
}

.add-btn {
  background: #4f46e5;
  color: #fff;
  border: none;
  padding: 10px 20px;
  border-radius: 10px;
  cursor: pointer;
}

.add-btn:hover {
  background: #4338ca;
}

.note-item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 12px;
  border-radius: 10px;
  margin-bottom: 10px;
}

.note-left {
  display: flex;
  align-items: center;
  gap: 12px;
}

.index {
  width: 32px;
  height: 32px;
  border-radius: 50%;
  background: #4f46e5;
  color: #fff;
  display: flex;
  align-items: center;
  justify-content: center;
  font-weight: bold;
}

.note-text {
  margin: 0;
  font-size: 15px;
}

.note-meta {
  margin: 4px 0 0;
  font-size: 13px;
  color: #666;
}

.高 {
  background: #fee2e2;
  border-left: 4px solid #ef4444;
}
.中 {
  background: #fef3c7;
  border-left: 4px solid #f59e0b;
}
.低 {
  background: #d1fae5;
  border-left: 4px solid #10b981;
}

.del-btn {
  background: #fff;
  color: #ef4444;
  border: 1px solid #fecaca;
  padding: 8px 14px;
  border-radius: 8px;
  cursor: pointer;
}

.del-btn:hover {
  background: #fef2f2;
}

.empty {
  color: #888;
  text-align: center;
}

.count {
  color: #4f46e5;
  font-weight: bold;
}
</style>
