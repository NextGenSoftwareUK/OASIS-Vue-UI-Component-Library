<script setup lang="ts">
defineProps<{ questName?: string; lat?: string; lng?: string; description?: string }>()
const emit = defineEmits<{ close: [] }>()
</script>
<template>
  <div class="p-shell">
    <div class="p-icon">🗺️</div>
    <h2 class="p-title">{{ questName ?? 'Quest Location' }}</h2>
    <div class="p-coords" v-if="lat || lng">
      <span class="p-coord-label">Coordinates</span>
      <span class="p-coord-value">{{ lat ?? '0.0' }}, {{ lng ?? '0.0' }}</span>
    </div>
    <p class="p-body" v-if="description">{{ description }}</p>
    <p class="p-body" v-else>Quest map integration is coming soon — you will be able to see quest locations, waypoints, and objectives overlaid on the Our World map.</p>
    <button class="p-btn" @click="emit('close')">Close</button>
  </div>
</template>
<style scoped>
.p-shell{display:flex;flex-direction:column;align-items:center;gap:16px;padding:32px 20px;text-align:center}.p-icon{font-size:44px}.p-title{font-family:'Orbitron',sans-serif;font-size:18px;color:#fff;margin:0}.p-coords{background:rgba(0,200,255,.06);border:1px solid rgba(0,200,255,.2);border-radius:8px;padding:10px 16px;display:flex;flex-direction:column;gap:4px}.p-coord-label{font-size:11px;color:#7a9bbf;font-weight:600;letter-spacing:.08em;text-transform:uppercase}.p-coord-value{font-family:'Orbitron',sans-serif;font-size:14px;color:#00c8ff}.p-body{font-size:14px;color:#a8bfd8;line-height:1.6;margin:0;max-width:360px}.p-btn{background:linear-gradient(135deg,#00c8ff,#0080ff);border:none;border-radius:8px;color:#fff;font-family:'Orbitron',sans-serif;font-size:12px;font-weight:700;letter-spacing:.08em;padding:11px 28px;cursor:pointer;transition:opacity .2s}.p-btn:hover{opacity:.85}
</style>
