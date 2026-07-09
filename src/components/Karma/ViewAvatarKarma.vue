<script setup lang="ts">
defineProps<{ username?: string; karma?: number; level?: string; positive?: number; negative?: number }>()
const emit = defineEmits<{ close: [] }>()
</script>
<template>
  <div class="p-shell">
    <div class="p-icon">⭐</div>
    <h2 class="p-title">{{ username ?? 'Avatar' }} Karma</h2>
    <div class="p-stats">
      <div class="p-stat p-stat--main"><span class="p-stat-label">Total Karma</span><span class="p-stat-value p-stat-value--gold">{{ karma ?? 0 }}</span></div>
      <div class="p-stat"><span class="p-stat-label">Level</span><span class="p-stat-value">{{ level ?? 'Initiate' }}</span></div>
      <div class="p-stat"><span class="p-stat-label">Positive</span><span class="p-stat-value p-stat-value--pos">+{{ positive ?? 0 }}</span></div>
      <div class="p-stat"><span class="p-stat-label">Negative</span><span class="p-stat-value p-stat-value--neg">-{{ negative ?? 0 }}</span></div>
    </div>
    <button class="p-btn" @click="emit('close')">Close</button>
  </div>
</template>
<style scoped>
.p-shell{display:flex;flex-direction:column;align-items:center;gap:18px;padding:32px 20px;text-align:center}.p-icon{font-size:50px}.p-title{font-family:'Orbitron',sans-serif;font-size:18px;color:#fff;margin:0}.p-stats{display:grid;grid-template-columns:1fr 1fr;gap:10px;width:100%;max-width:340px}.p-stat{background:rgba(255,255,255,.04);border:1px solid rgba(0,200,255,.15);border-radius:10px;padding:12px 16px;display:flex;flex-direction:column;gap:4px}.p-stat--main{grid-column:span 2}.p-stat-label{font-size:11px;color:#7a9bbf;font-weight:600;letter-spacing:.08em;text-transform:uppercase}.p-stat-value{font-family:'Orbitron',sans-serif;font-size:20px;color:#fff;font-weight:700}.p-stat-value--gold{color:#ffb43c}.p-stat-value--pos{color:#00e676;font-size:16px}.p-stat-value--neg{color:#ff4444;font-size:16px}.p-btn{background:linear-gradient(135deg,#00c8ff,#0080ff);border:none;border-radius:8px;color:#fff;font-family:'Orbitron',sans-serif;font-size:12px;font-weight:700;letter-spacing:.08em;padding:11px 28px;cursor:pointer;transition:opacity .2s}.p-btn:hover{opacity:.85}
</style>
