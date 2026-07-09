<script setup lang="ts">
const emit = defineEmits<{ close: [] }>()
const providers = [
  { name: 'Holochain', status: 'Active', type: 'P2P', priority: 1 },
  { name: 'MongoDB', status: 'Active', type: 'Database', priority: 2 },
  { name: 'IPFS', status: 'Standby', type: 'File', priority: 3 },
  { name: 'Ethereum', status: 'Inactive', type: 'Blockchain', priority: 4 },
]
</script>
<template>
  <div class="p-shell">
    <h2 class="p-title">⚙️ Manage Providers</h2>
    <div class="p-list">
      <div v-for="p in providers" :key="p.name" class="p-item">
        <div class="p-item-info">
          <span class="p-item-name">{{ p.name }}</span>
          <span class="p-item-type">{{ p.type }} · Priority {{ p.priority }}</span>
        </div>
        <span class="p-status" :class="`p-status--${p.status.toLowerCase()}`">{{ p.status }}</span>
      </div>
    </div>
    <button class="p-btn" @click="emit('close')">Close</button>
  </div>
</template>
<style scoped>
.p-shell{display:flex;flex-direction:column;gap:18px;padding:24px 20px}.p-title{font-family:'Orbitron',sans-serif;font-size:18px;color:#fff;margin:0}.p-list{display:flex;flex-direction:column;gap:8px}.p-item{display:flex;align-items:center;justify-content:space-between;background:rgba(255,255,255,.04);border:1px solid rgba(0,200,255,.12);border-radius:10px;padding:12px 14px}.p-item-info{display:flex;flex-direction:column;gap:3px}.p-item-name{font-family:'Orbitron',sans-serif;font-size:13px;color:#fff;font-weight:700}.p-item-type{font-size:11px;color:#7a9bbf}.p-status{font-size:11px;font-weight:700;letter-spacing:.06em;border-radius:999px;padding:3px 10px;border:1px solid currentColor;text-transform:uppercase}.p-status--active{color:#00e676}.p-status--standby{color:#ffb43c}.p-status--inactive{color:#5a7a9a}.p-btn{align-self:flex-end;background:linear-gradient(135deg,#00c8ff,#0080ff);border:none;border-radius:8px;color:#fff;font-family:'Orbitron',sans-serif;font-size:12px;font-weight:700;letter-spacing:.08em;padding:10px 24px;cursor:pointer;transition:opacity .2s}.p-btn:hover{opacity:.85}
</style>
