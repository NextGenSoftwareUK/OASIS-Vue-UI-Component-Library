<script setup lang="ts">
defineProps<{ name?: string; tokenId?: string; owner?: string; provider?: string; description?: string }>()
const emit = defineEmits<{ close: [] }>()
</script>
<template>
  <div class="p-shell">
    <div class="p-nft-preview">🖼️</div>
    <h2 class="p-title">{{ name ?? 'OASIS NFT' }}</h2>
    <div class="p-details">
      <div class="p-detail"><span class="p-detail-label">Token ID</span><span class="p-detail-value">{{ tokenId ?? '#0001' }}</span></div>
      <div class="p-detail"><span class="p-detail-label">Owner</span><span class="p-detail-value">{{ owner ?? 'Unknown' }}</span></div>
      <div class="p-detail"><span class="p-detail-label">Provider</span><span class="p-detail-value">{{ provider ?? 'Ethereum' }}</span></div>
    </div>
    <p class="p-body">{{ description ?? 'A unique OASIS NFT existing across the decentralised web.' }}</p>
    <button class="p-btn" @click="emit('close')">Close</button>
  </div>
</template>
<style scoped>
.p-shell{display:flex;flex-direction:column;align-items:center;gap:16px;padding:32px 20px;text-align:center}.p-nft-preview{width:100px;height:100px;background:linear-gradient(135deg,rgba(0,200,255,.1),rgba(184,127,255,.1));border:1px solid rgba(0,200,255,.2);border-radius:12px;display:flex;align-items:center;justify-content:center;font-size:40px}.p-title{font-family:'Orbitron',sans-serif;font-size:18px;color:#fff;margin:0}.p-details{display:flex;gap:12px;flex-wrap:wrap;justify-content:center}.p-detail{background:rgba(255,255,255,.04);border:1px solid rgba(0,200,255,.15);border-radius:10px;padding:10px 14px;display:flex;flex-direction:column;gap:4px;text-align:center}.p-detail-label{font-size:11px;color:#7a9bbf;font-weight:600;letter-spacing:.08em;text-transform:uppercase}.p-detail-value{font-family:'Orbitron',sans-serif;font-size:13px;color:#fff;font-weight:700}.p-body{font-size:13px;color:#a8bfd8;line-height:1.6;margin:0;max-width:360px}.p-btn{background:linear-gradient(135deg,#00c8ff,#0080ff);border:none;border-radius:8px;color:#fff;font-family:'Orbitron',sans-serif;font-size:12px;font-weight:700;letter-spacing:.08em;padding:11px 28px;cursor:pointer;transition:opacity .2s}.p-btn:hover{opacity:.85}
</style>
