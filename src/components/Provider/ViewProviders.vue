<script setup lang="ts">
const emit = defineEmits<{ close: [] }>()
const providers = [
  { name: 'Holochain', type: 'P2P', status: 'Active', icon: '🔮' },
  { name: 'MongoDB', type: 'Database', status: 'Active', icon: '🍃' },
  { name: 'IPFS', type: 'File', status: 'Active', icon: '📁' },
  { name: 'Ethereum', type: 'Blockchain', status: 'Inactive', icon: '💎' },
  { name: 'Neo4j', type: 'Graph DB', status: 'Active', icon: '🕸️' },
  { name: 'SQLite', type: 'Local DB', status: 'Active', icon: '🗄️' },
  { name: 'SEEDS', type: 'Blockchain', status: 'Inactive', icon: '🌱' },
  { name: 'Solid', type: 'Data Pod', status: 'Standby', icon: '💠' },
]
</script>
<template>
  <div class="p-shell">
    <h2 class="p-title">🔌 All Providers</h2>
    <div class="p-grid">
      <div v-for="p in providers" :key="p.name" class="p-card">
        <span class="p-card-icon">{{ p.icon }}</span>
        <span class="p-card-name">{{ p.name }}</span>
        <span class="p-card-type">{{ p.type }}</span>
        <span class="p-status" :class="`p-status--${p.status.toLowerCase()}`">{{ p.status }}</span>
      </div>
    </div>
    <button class="p-btn" @click="emit('close')">Close</button>
  </div>
</template>
<style scoped>
.p-shell{display:flex;flex-direction:column;gap:18px;padding:24px 20px}.p-title{font-family:'Orbitron',sans-serif;font-size:18px;color:#fff;margin:0}.p-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(140px,1fr));gap:10px}.p-card{background:rgba(255,255,255,.04);border:1px solid rgba(0,200,255,.12);border-radius:10px;padding:14px 10px;display:flex;flex-direction:column;align-items:center;gap:6px;text-align:center}.p-card-icon{font-size:24px}.p-card-name{font-family:'Orbitron',sans-serif;font-size:11px;color:#fff;font-weight:700}.p-card-type{font-size:10px;color:#7a9bbf}.p-status{font-size:10px;font-weight:700;letter-spacing:.06em;border-radius:999px;padding:3px 8px;border:1px solid currentColor;text-transform:uppercase}.p-status--active{color:#00e676}.p-status--standby{color:#ffb43c}.p-status--inactive{color:#5a7a9a}.p-btn{align-self:flex-end;background:linear-gradient(135deg,#00c8ff,#0080ff);border:none;border-radius:8px;color:#fff;font-family:'Orbitron',sans-serif;font-size:12px;font-weight:700;letter-spacing:.08em;padding:10px 24px;cursor:pointer;transition:opacity .2s}.p-btn:hover{opacity:.85}
</style>
