<script setup lang="ts">
const emit = defineEmits<{ close: []; download: [] }>()
</script>
<template>
  <div class="p-shell">
    <div class="p-icon">🌍</div>
    <h2 class="p-title">Download Our World</h2>
    <p class="p-body">Download the full Our World map for offline use, including all quest locations, 3D objects, and HolON data embedded in the terrain.</p>
    <div class="p-size">Estimated size: <strong>2.4 GB</strong></div>
    <div class="p-actions">
      <button class="p-btn-cancel" type="button" @click="emit('close')">Cancel</button>
      <button class="p-btn" @click="emit('download')">Download</button>
    </div>
  </div>
</template>
<style scoped>
.p-shell{display:flex;flex-direction:column;align-items:center;gap:16px;padding:32px 20px;text-align:center}.p-icon{font-size:54px}.p-title{font-family:'Orbitron',sans-serif;font-size:18px;color:#fff;margin:0}.p-body{font-size:14px;color:#a8bfd8;line-height:1.6;margin:0;max-width:360px}.p-size{font-size:13px;color:#7a9bbf;background:rgba(0,200,255,.06);border:1px solid rgba(0,200,255,.15);border-radius:8px;padding:8px 16px}.p-actions{display:flex;gap:12px}.p-btn{background:linear-gradient(135deg,#00c8ff,#0080ff);border:none;border-radius:8px;color:#fff;font-family:'Orbitron',sans-serif;font-size:12px;font-weight:700;letter-spacing:.08em;padding:11px 28px;cursor:pointer;transition:opacity .2s}.p-btn:hover{opacity:.85}.p-btn-cancel{background:transparent;border:1px solid rgba(0,200,255,.3);border-radius:8px;color:#00c8ff;font-family:'Orbitron',sans-serif;font-size:12px;font-weight:700;letter-spacing:.08em;padding:11px 28px;cursor:pointer}
</style>
