<script setup lang="ts">
defineProps<{ providerName?: string }>()
const emit = defineEmits<{ close: [] }>()
const stats = [
  { label: 'Total Reads', value: '1,248,530' },
  { label: 'Total Writes', value: '524,120' },
  { label: 'Avg Response', value: '12ms' },
  { label: 'Uptime', value: '99.97%' },
  { label: 'Data Stored', value: '14.2 GB' },
  { label: 'Active Connections', value: '342' },
]
</script>
<template>
  <div class="p-shell">
    <h2 class="p-title">📊 {{ providerName ?? 'Provider' }} Stats</h2>
    <div class="p-grid">
      <div v-for="s in stats" :key="s.label" class="p-stat">
        <span class="p-stat-label">{{ s.label }}</span>
        <span class="p-stat-value">{{ s.value }}</span>
      </div>
    </div>
    <button class="p-btn" @click="emit('close')">Close</button>
  </div>
</template>
<style scoped>
.p-shell{display:flex;flex-direction:column;gap:18px;padding:24px 20px}.p-title{font-family:'Orbitron',sans-serif;font-size:18px;color:#fff;margin:0}.p-grid{display:grid;grid-template-columns:1fr 1fr;gap:10px}.p-stat{background:rgba(0,200,255,.04);border:1px solid rgba(0,200,255,.12);border-radius:10px;padding:14px;display:flex;flex-direction:column;gap:6px}.p-stat-label{font-size:11px;color:#7a9bbf;font-weight:600;letter-spacing:.06em;text-transform:uppercase}.p-stat-value{font-family:'Orbitron',sans-serif;font-size:18px;color:#fff;font-weight:700}.p-btn{align-self:flex-end;background:linear-gradient(135deg,#00c8ff,#0080ff);border:none;border-radius:8px;color:#fff;font-family:'Orbitron',sans-serif;font-size:12px;font-weight:700;letter-spacing:.08em;padding:10px 24px;cursor:pointer;transition:opacity .2s}.p-btn:hover{opacity:.85}
</style>
