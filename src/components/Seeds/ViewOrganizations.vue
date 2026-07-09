<script setup lang="ts">
const emit = defineEmits<{ close: [] }>()
const orgs = [
  { name: 'SEEDS Foundation', members: 12400, type: 'Foundation', status: 'Active' },
  { name: 'OASIS Collective', members: 3200, type: 'Collective', status: 'Active' },
  { name: 'Our World Community', members: 8900, type: 'Community', status: 'Active' },
  { name: 'Earth Regenerators', members: 5600, type: 'Movement', status: 'Growing' },
]
</script>
<template>
  <div class="p-shell">
    <h2 class="p-title">🌿 SEEDS Organizations</h2>
    <div class="p-list">
      <div v-for="o in orgs" :key="o.name" class="p-item">
        <div class="p-item-info">
          <span class="p-item-name">{{ o.name }}</span>
          <span class="p-item-desc">{{ o.type }} · {{ o.members.toLocaleString() }} members</span>
        </div>
        <span class="p-status" :class="`p-status--${o.status.toLowerCase()}`">{{ o.status }}</span>
      </div>
    </div>
    <button class="p-btn" @click="emit('close')">Close</button>
  </div>
</template>
<style scoped>
.p-shell{display:flex;flex-direction:column;gap:18px;padding:24px 20px}.p-title{font-family:'Orbitron',sans-serif;font-size:18px;color:#fff;margin:0}.p-list{display:flex;flex-direction:column;gap:8px}.p-item{display:flex;align-items:center;justify-content:space-between;background:rgba(255,255,255,.04);border:1px solid rgba(0,200,255,.12);border-radius:10px;padding:12px 14px}.p-item-info{display:flex;flex-direction:column;gap:3px}.p-item-name{font-family:'Orbitron',sans-serif;font-size:13px;color:#fff;font-weight:700}.p-item-desc{font-size:12px;color:#7a9bbf}.p-status{font-size:11px;font-weight:700;letter-spacing:.06em;border-radius:999px;padding:3px 10px;border:1px solid currentColor;text-transform:uppercase}.p-status--active{color:#00e676}.p-status--growing{color:#ffb43c}.p-btn{align-self:flex-end;background:linear-gradient(135deg,#00c8ff,#0080ff);border:none;border-radius:8px;color:#fff;font-family:'Orbitron',sans-serif;font-size:12px;font-weight:700;letter-spacing:.08em;padding:10px 24px;cursor:pointer;transition:opacity .2s}.p-btn:hover{opacity:.85}
</style>
