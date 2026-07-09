<script setup lang="ts">
defineProps<{ name?: string; price?: string; imageUrl?: string; provider?: string }>()
const emit = defineEmits<{ close: []; purchase: [] }>()
</script>
<template>
  <div class="p-shell">
    <div class="p-nft-preview">{{ imageUrl ? '' : '🖼️' }}</div>
    <h2 class="p-title">{{ name ?? 'OASIS NFT' }}</h2>
    <div class="p-details">
      <div class="p-detail"><span class="p-detail-label">Price</span><span class="p-detail-value">{{ price ?? '0.1 ETH' }}</span></div>
      <div class="p-detail"><span class="p-detail-label">Provider</span><span class="p-detail-value">{{ provider ?? 'Ethereum' }}</span></div>
    </div>
    <div class="p-actions">
      <button class="p-btn-cancel" @click="emit('close')">Cancel</button>
      <button class="p-btn" @click="emit('purchase')">Purchase</button>
    </div>
  </div>
</template>
<style scoped>
.p-shell{display:flex;flex-direction:column;align-items:center;gap:18px;padding:32px 20px;text-align:center}.p-nft-preview{width:120px;height:120px;background:linear-gradient(135deg,rgba(0,200,255,.1),rgba(184,127,255,.1));border:1px solid rgba(0,200,255,.2);border-radius:12px;display:flex;align-items:center;justify-content:center;font-size:48px}.p-title{font-family:'Orbitron',sans-serif;font-size:18px;color:#fff;margin:0}.p-details{display:flex;gap:16px}.p-detail{background:rgba(255,255,255,.04);border:1px solid rgba(0,200,255,.15);border-radius:10px;padding:12px 18px;display:flex;flex-direction:column;gap:4px}.p-detail-label{font-size:11px;color:#7a9bbf;font-weight:600;letter-spacing:.08em;text-transform:uppercase}.p-detail-value{font-family:'Orbitron',sans-serif;font-size:15px;color:#fff;font-weight:700}.p-actions{display:flex;gap:12px}.p-btn{background:linear-gradient(135deg,#00c8ff,#0080ff);border:none;border-radius:8px;color:#fff;font-family:'Orbitron',sans-serif;font-size:12px;font-weight:700;letter-spacing:.08em;padding:11px 28px;cursor:pointer;transition:opacity .2s}.p-btn:hover{opacity:.85}.p-btn-cancel{background:transparent;border:1px solid rgba(0,200,255,.3);border-radius:8px;color:#00c8ff;font-family:'Orbitron',sans-serif;font-size:12px;font-weight:700;letter-spacing:.08em;padding:11px 28px;cursor:pointer}
</style>
