<script setup lang="ts">
import { ref } from 'vue'
const emit = defineEmits<{ close: []; submit: [{ query: string; status: string; difficulty: string }] }>()
const form = ref({ query: '', status: 'All', difficulty: 'All' })
function handleSubmit() { emit('submit', { ...form.value }) }
</script>
<template>
  <div class="p-shell">
    <h2 class="p-title">🔍 Search Quest</h2>
    <form class="p-form" @submit.prevent="handleSubmit">
      <div class="p-row"><label class="p-label">Quest Name</label><input class="p-input" v-model="form.query" placeholder="Search quests..." /></div>
      <div class="p-row">
        <label class="p-label">Status</label>
        <select class="p-input" v-model="form.status">
          <option>All</option><option>Available</option><option>Active</option><option>Completed</option>
        </select>
      </div>
      <div class="p-row">
        <label class="p-label">Difficulty</label>
        <select class="p-input" v-model="form.difficulty">
          <option>All</option><option>Easy</option><option>Medium</option><option>Hard</option><option>Legendary</option>
        </select>
      </div>
      <div class="p-actions"><button class="p-btn-cancel" type="button" @click="emit('close')">Cancel</button><button class="p-btn" type="submit">Search</button></div>
    </form>
  </div>
</template>
<style scoped>
.p-shell{display:flex;flex-direction:column;gap:20px;padding:24px 20px}.p-title{font-family:'Orbitron',sans-serif;font-size:18px;color:#fff;margin:0}.p-form{display:flex;flex-direction:column;gap:14px}.p-row{display:flex;flex-direction:column;gap:6px}.p-label{font-size:12px;color:#7a9bbf;font-weight:600;letter-spacing:.05em}.p-input{background:rgba(255,255,255,.06);border:1px solid rgba(0,200,255,.2);border-radius:8px;color:#fff;font-size:14px;padding:10px 12px;width:100%;box-sizing:border-box;outline:none;transition:border-color .2s}.p-input:focus{border-color:rgba(0,200,255,.5)}.p-actions{display:flex;gap:10px;justify-content:flex-end;margin-top:4px}.p-btn{background:linear-gradient(135deg,#00c8ff,#0080ff);border:none;border-radius:8px;color:#fff;font-family:'Orbitron',sans-serif;font-size:12px;font-weight:700;letter-spacing:.08em;padding:10px 24px;cursor:pointer;transition:opacity .2s}.p-btn:hover{opacity:.85}.p-btn-cancel{background:transparent;border:1px solid rgba(0,200,255,.3);border-radius:8px;color:#00c8ff;font-family:'Orbitron',sans-serif;font-size:12px;font-weight:700;letter-spacing:.08em;padding:10px 24px;cursor:pointer}
</style>
