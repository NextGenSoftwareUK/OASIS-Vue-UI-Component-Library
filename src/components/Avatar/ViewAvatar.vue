<script setup lang="ts">
defineProps<{ username?: string; level?: number; karma?: number; provider?: string }>()
const emit = defineEmits<{ close: [] }>()
</script>
<template>
  <div class="p-shell">
    <div class="p-avatar-icon">👤</div>
    <h2 class="p-title">{{ username ?? 'Avatar Profile' }}</h2>
    <div class="p-stats">
      <div class="p-stat"><span class="p-stat-label">Level</span><span class="p-stat-value">{{ level ?? 1 }}</span></div>
      <div class="p-stat"><span class="p-stat-label">Karma</span><span class="p-stat-value">{{ karma ?? 0 }}</span></div>
      <div class="p-stat"><span class="p-stat-label">Provider</span><span class="p-stat-value">{{ provider ?? 'Holochain' }}</span></div>
    </div>
    <button class="p-btn" @click="emit('close')">Close</button>
  </div>
</template>
<style scoped>
.p-shell{display:flex;flex-direction:column;align-items:center;gap:18px;padding:32px 20px;text-align:center}.p-avatar-icon{font-size:60px}.p-title{font-family:'Orbitron',sans-serif;font-size:20px;color:#fff;margin:0}.p-stats{display:flex;gap:24px}.p-stat{display:flex;flex-direction:column;gap:4px;align-items:center;background:rgba(0,200,255,.06);border:1px solid rgba(0,200,255,.15);border-radius:10px;padding:12px 18px}.p-stat-label{font-size:11px;color:#7a9bbf;font-weight:600;letter-spacing:.08em;text-transform:uppercase}.p-stat-value{font-family:'Orbitron',sans-serif;font-size:16px;color:#00c8ff;font-weight:700}.p-btn{background:linear-gradient(135deg,#00c8ff,#0080ff);border:none;border-radius:8px;color:#fff;font-family:'Orbitron',sans-serif;font-size:12px;font-weight:700;letter-spacing:.08em;padding:11px 28px;cursor:pointer;transition:opacity .2s}.p-btn:hover{opacity:.85}
</style>
