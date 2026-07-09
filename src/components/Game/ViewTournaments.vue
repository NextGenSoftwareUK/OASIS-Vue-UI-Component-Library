<script setup lang="ts">
const emit = defineEmits<{ close: [] }>()
const tournaments = [
  { name: 'OASIS Grand Prix', date: '2025-03-01', prize: '5000 KARMA', status: 'Open', icon: '🏁' },
  { name: 'Quantum Arena Cup', date: '2025-04-15', prize: '2000 SEEDS', status: 'Upcoming', icon: '⚡' },
  { name: 'Starlight Championship', date: '2025-02-10', prize: '1000 KARMA', status: 'Ended', icon: '⭐' },
]
</script>
<template>
  <div class="p-shell">
    <h2 class="p-title">🏁 Tournaments</h2>
    <div class="p-list">
      <div v-for="t in tournaments" :key="t.name" class="p-item">
        <span class="p-item-icon">{{ t.icon }}</span>
        <div class="p-item-info">
          <span class="p-item-name">{{ t.name }}</span>
          <span class="p-item-desc">{{ t.date }} · Prize: {{ t.prize }}</span>
        </div>
        <span class="p-status" :class="`p-status--${t.status.toLowerCase()}`">{{ t.status }}</span>
      </div>
    </div>
    <button class="p-btn" @click="emit('close')">Close</button>
  </div>
</template>
<style scoped>
.p-shell{display:flex;flex-direction:column;gap:18px;padding:24px 20px}.p-title{font-family:'Orbitron',sans-serif;font-size:18px;color:#fff;margin:0}.p-list{display:flex;flex-direction:column;gap:10px}.p-item{display:flex;align-items:center;gap:14px;background:rgba(255,255,255,.04);border:1px solid rgba(0,200,255,.15);border-radius:10px;padding:14px}.p-item-icon{font-size:28px;flex-shrink:0}.p-item-info{display:flex;flex-direction:column;gap:3px;flex:1}.p-item-name{font-family:'Orbitron',sans-serif;font-size:13px;color:#fff;font-weight:700}.p-item-desc{font-size:12px;color:#7a9bbf}.p-status{font-size:11px;font-weight:700;letter-spacing:.06em;border-radius:999px;padding:4px 10px;border:1px solid currentColor}.p-status--open{color:#00c8ff}.p-status--upcoming{color:#ffb43c}.p-status--ended{color:#5a7a9a}.p-btn{align-self:flex-end;background:linear-gradient(135deg,#00c8ff,#0080ff);border:none;border-radius:8px;color:#fff;font-family:'Orbitron',sans-serif;font-size:12px;font-weight:700;letter-spacing:.08em;padding:10px 24px;cursor:pointer;transition:opacity .2s}.p-btn:hover{opacity:.85}
</style>
