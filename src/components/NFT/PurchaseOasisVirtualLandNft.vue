<script setup lang="ts">
defineProps<{ parcelId?: string; size?: string; price?: string; coordinates?: string }>()
const emit = defineEmits<{ close: []; purchase: [] }>()
</script>
<template>
  <div class="p-shell">
    <div class="p-icon">🏝️</div>
    <h2 class="p-title">Purchase Virtual Land NFT</h2>
    <div class="p-details">
      <div class="p-detail"><span class="p-detail-label">Parcel ID</span><span class="p-detail-value">{{ parcelId ?? '#LAND-001' }}</span></div>
      <div class="p-detail"><span class="p-detail-label">Size</span><span class="p-detail-value">{{ size ?? '1 km²' }}</span></div>
      <div class="p-detail"><span class="p-detail-label">Coordinates</span><span class="p-detail-value">{{ coordinates ?? '51.5, -0.1' }}</span></div>
      <div class="p-detail"><span class="p-detail-label">Price</span><span class="p-detail-value p-detail-value--gold">{{ price ?? '0.5 ETH' }}</span></div>
    </div>
    <div class="p-actions">
      <button class="p-btn-cancel" @click="emit('close')">Cancel</button>
      <button class="p-btn" @click="emit('purchase')">Purchase Land</button>
    </div>
  </div>
</template>
<style scoped>
.p-shell{display:flex;flex-direction:column;align-items:center;gap:18px;padding:32px 20px;text-align:center}.p-icon{font-size:54px}.p-title{font-family:'Orbitron',sans-serif;font-size:18px;color:#fff;margin:0}.p-details{display:grid;grid-template-columns:1fr 1fr;gap:10px;width:100%;max-width:340px}.p-detail{background:rgba(255,255,255,.04);border:1px solid rgba(0,200,255,.15);border-radius:10px;padding:12px 16px;display:flex;flex-direction:column;gap:4px;text-align:center}.p-detail-label{font-size:11px;color:#7a9bbf;font-weight:600;letter-spacing:.08em;text-transform:uppercase}.p-detail-value{font-family:'Orbitron',sans-serif;font-size:14px;color:#fff;font-weight:700}.p-detail-value--gold{color:#ffb43c}.p-actions{display:flex;gap:12px}.p-btn{background:linear-gradient(135deg,#00c8ff,#0080ff);border:none;border-radius:8px;color:#fff;font-family:'Orbitron',sans-serif;font-size:12px;font-weight:700;letter-spacing:.08em;padding:11px 28px;cursor:pointer;transition:opacity .2s}.p-btn:hover{opacity:.85}.p-btn-cancel{background:transparent;border:1px solid rgba(0,200,255,.3);border-radius:8px;color:#00c8ff;font-family:'Orbitron',sans-serif;font-size:12px;font-weight:700;letter-spacing:.08em;padding:11px 28px;cursor:pointer}
</style>
