<script setup lang="ts">
defineProps<{ name?: string; version?: string; size?: string }>()
const emit = defineEmits<{ close: []; install: [] }>()
</script>
<template>
  <div class="p-shell">
    <div class="p-icon">📦</div>
    <h2 class="p-title">Install OAPP</h2>
    <div class="p-card">
      <div class="p-card-row"><span class="p-card-label">Name</span><span class="p-card-value">{{ name ?? 'OAPP' }}</span></div>
      <div class="p-card-row"><span class="p-card-label">Version</span><span class="p-card-value">{{ version ?? '1.0.0' }}</span></div>
      <div class="p-card-row"><span class="p-card-label">Size</span><span class="p-card-value">{{ size ?? '2.3 MB' }}</span></div>
    </div>
    <p class="p-body">This OAPP will be installed to your OASIS avatar and made available in Our World.</p>
    <div class="p-actions">
      <button class="p-btn-cancel" @click="emit('close')">Cancel</button>
      <button class="p-btn" @click="emit('install')">Install</button>
    </div>
  </div>
</template>
<style scoped>
.p-shell{display:flex;flex-direction:column;align-items:center;gap:16px;padding:32px 20px;text-align:center}.p-icon{font-size:48px}.p-title{font-family:'Orbitron',sans-serif;font-size:18px;color:#fff;margin:0}.p-card{width:100%;max-width:300px;background:rgba(0,200,255,.04);border:1px solid rgba(0,200,255,.15);border-radius:10px;overflow:hidden}.p-card-row{display:flex;justify-content:space-between;align-items:center;padding:10px 14px;border-bottom:1px solid rgba(0,200,255,.08)}.p-card-row:last-child{border-bottom:none}.p-card-label{font-size:12px;color:#7a9bbf;font-weight:600}.p-card-value{font-size:13px;color:#fff;font-weight:600}.p-body{font-size:13px;color:#a8bfd8;line-height:1.6;margin:0;max-width:340px}.p-actions{display:flex;gap:12px}.p-btn{background:linear-gradient(135deg,#00c8ff,#0080ff);border:none;border-radius:8px;color:#fff;font-family:'Orbitron',sans-serif;font-size:12px;font-weight:700;letter-spacing:.08em;padding:11px 28px;cursor:pointer;transition:opacity .2s}.p-btn:hover{opacity:.85}.p-btn-cancel{background:transparent;border:1px solid rgba(0,200,255,.3);border-radius:8px;color:#00c8ff;font-family:'Orbitron',sans-serif;font-size:12px;font-weight:700;letter-spacing:.08em;padding:11px 28px;cursor:pointer}
</style>
