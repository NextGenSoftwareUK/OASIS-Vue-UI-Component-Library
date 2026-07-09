<script setup lang="ts">
const emit = defineEmits<{ close: [] }>()
const providers = [
  { name: 'Holochain', read: 95, write: 92, score: 94 },
  { name: 'MongoDB', read: 88, write: 85, score: 87 },
  { name: 'SQLite', read: 99, write: 96, score: 98 },
  { name: 'IPFS', read: 60, write: 45, score: 53 },
  { name: 'Ethereum', read: 40, write: 30, score: 35 },
]
</script>
<template>
  <div class="p-shell">
    <h2 class="p-title">⚡ Compare Provider Speeds</h2>
    <div class="p-table-wrap">
      <table class="p-table">
        <thead><tr><th>Provider</th><th>Read</th><th>Write</th><th>Score</th></tr></thead>
        <tbody>
          <tr v-for="p in providers" :key="p.name">
            <td>{{ p.name }}</td>
            <td><div class="p-bar-wrap"><div class="p-bar" :style="{ width: p.read + '%' }"></div><span>{{ p.read }}</span></div></td>
            <td><div class="p-bar-wrap"><div class="p-bar p-bar--write" :style="{ width: p.write + '%' }"></div><span>{{ p.write }}</span></div></td>
            <td class="p-score">{{ p.score }}</td>
          </tr>
        </tbody>
      </table>
    </div>
    <button class="p-btn" @click="emit('close')">Close</button>
  </div>
</template>
<style scoped>
.p-shell{display:flex;flex-direction:column;gap:18px;padding:24px 20px}.p-title{font-family:'Orbitron',sans-serif;font-size:18px;color:#fff;margin:0}.p-table-wrap{overflow-x:auto;border-radius:10px;border:1px solid rgba(0,200,255,.15)}.p-table{width:100%;border-collapse:collapse;font-size:13px}.p-table th{background:rgba(0,200,255,.08);color:#00c8ff;font-family:'Orbitron',sans-serif;font-size:11px;font-weight:700;letter-spacing:.06em;padding:10px 12px;text-align:left}.p-table td{color:#c8dff0;padding:9px 12px;border-top:1px solid rgba(255,255,255,.05)}.p-bar-wrap{display:flex;align-items:center;gap:8px}.p-bar{height:6px;border-radius:999px;background:linear-gradient(90deg,#00c8ff,#0080ff);transition:width .4s}.p-bar--write{background:linear-gradient(90deg,#b87fff,#7040cc)}.p-score{color:#ffb43c;font-family:'Orbitron',sans-serif;font-weight:700}.p-btn{align-self:flex-end;background:linear-gradient(135deg,#00c8ff,#0080ff);border:none;border-radius:8px;color:#fff;font-family:'Orbitron',sans-serif;font-size:12px;font-weight:700;letter-spacing:.08em;padding:10px 24px;cursor:pointer;transition:opacity .2s}.p-btn:hover{opacity:.85}
</style>
