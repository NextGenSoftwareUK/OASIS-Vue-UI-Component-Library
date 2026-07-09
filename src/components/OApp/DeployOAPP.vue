<script setup lang="ts">
defineProps<{ name?: string; version?: string }>()
const emit = defineEmits<{ close: []; deploy: [] }>()
</script>
<template>
  <div class="p-shell">
    <div class="p-icon">🚀</div>
    <h2 class="p-title">Deploy OAPP</h2>
    <p class="p-body">Ready to deploy <strong>{{ name ?? 'this OAPP' }}</strong> v{{ version ?? '1.0.0' }} to the OASIS network?</p>
    <div class="p-checklist">
      <div class="p-check">✅ Code compiled</div>
      <div class="p-check">✅ Tests passed</div>
      <div class="p-check">✅ Provider configured</div>
    </div>
    <div class="p-actions">
      <button class="p-btn-cancel" @click="emit('close')">Cancel</button>
      <button class="p-btn" @click="emit('deploy')">Deploy</button>
    </div>
  </div>
</template>
<style scoped>
.p-shell{display:flex;flex-direction:column;align-items:center;gap:16px;padding:32px 20px;text-align:center}.p-icon{font-size:48px}.p-title{font-family:'Orbitron',sans-serif;font-size:18px;color:#fff;margin:0}.p-body{font-size:14px;color:#a8bfd8;line-height:1.6;margin:0;max-width:360px}.p-checklist{display:flex;flex-direction:column;gap:8px;align-self:stretch;background:rgba(0,200,255,.04);border:1px solid rgba(0,200,255,.12);border-radius:10px;padding:14px}.p-check{font-size:13px;color:#c8dff0;text-align:left}.p-actions{display:flex;gap:12px}.p-btn{background:linear-gradient(135deg,#00c8ff,#0080ff);border:none;border-radius:8px;color:#fff;font-family:'Orbitron',sans-serif;font-size:12px;font-weight:700;letter-spacing:.08em;padding:11px 28px;cursor:pointer;transition:opacity .2s}.p-btn:hover{opacity:.85}.p-btn-cancel{background:transparent;border:1px solid rgba(0,200,255,.3);border-radius:8px;color:#00c8ff;font-family:'Orbitron',sans-serif;font-size:12px;font-weight:700;letter-spacing:.08em;padding:11px 28px;cursor:pointer}
</style>
