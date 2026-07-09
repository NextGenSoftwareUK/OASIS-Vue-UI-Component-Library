<script setup lang="ts">
const emit = defineEmits<{ close: [] }>()
</script>
<template>
  <div class="p-shell">
    <div class="p-icon">🗄️</div>
    <h2 class="p-title">SQLite Provider</h2>
    <p class="p-body">SQLite integration with the OASIS — a lightweight local database provider for offline and edge-device OASIS deployments with full SQL query support.</p>
    <button class="p-btn" @click="emit('close')">OK</button>
  </div>
</template>
<style scoped>
.p-shell{display:flex;flex-direction:column;align-items:center;gap:16px;padding:32px 20px;text-align:center}.p-icon{font-size:44px}.p-title{font-family:'Orbitron',sans-serif;font-size:18px;color:#fff;margin:0}.p-body{font-size:14px;color:#a8bfd8;line-height:1.6;margin:0;max-width:360px}.p-btn{background:linear-gradient(135deg,#00c8ff,#0080ff);border:none;border-radius:8px;color:#fff;font-family:'Orbitron',sans-serif;font-size:12px;font-weight:700;letter-spacing:.08em;padding:11px 28px;cursor:pointer;transition:opacity .2s}.p-btn:hover{opacity:.85}
</style>
