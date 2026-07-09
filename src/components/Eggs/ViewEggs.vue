<script setup lang="ts">
defineProps<{ name?: string; rarity?: string; hatchProgress?: number; reward?: string }>()
const emit = defineEmits<{ close: [] }>()
</script>
<template>
  <div class="p-shell">
    <div class="p-icon">{{ (hatchProgress ?? 0) >= 100 ? '🐣' : '🥚' }}</div>
    <h2 class="p-title">{{ name ?? 'Cosmic Egg' }}</h2>
    <div class="p-badge" :class="`p-badge--${(rarity ?? 'common').toLowerCase()}`">{{ rarity ?? 'Common' }}</div>
    <div class="p-progress-wrap" v-if="(hatchProgress ?? 0) < 100">
      <div class="p-progress-bar"><div class="p-progress-fill" :style="{ width: (hatchProgress ?? 0) + '%' }"></div></div>
      <span class="p-pct">{{ hatchProgress ?? 0 }}% incubated</span>
    </div>
    <p class="p-reward" v-if="(hatchProgress ?? 0) >= 100">✨ {{ reward ?? 'Mystery Companion' }}</p>
    <button class="p-btn" @click="emit('close')">Close</button>
  </div>
</template>
<style scoped>
.p-shell{display:flex;flex-direction:column;align-items:center;gap:16px;padding:32px 20px;text-align:center}.p-icon{font-size:64px}.p-title{font-family:'Orbitron',sans-serif;font-size:18px;color:#fff;margin:0}.p-badge{font-size:11px;font-weight:700;letter-spacing:.1em;text-transform:uppercase;border-radius:999px;padding:4px 12px;border:1px solid currentColor}.p-badge--common{color:#7a9bbf}.p-badge--rare{color:#5ba8ff}.p-badge--epic{color:#b87fff}.p-badge--legendary{color:#ffb43c}.p-progress-wrap{width:200px;display:flex;flex-direction:column;gap:6px;align-items:center}.p-progress-bar{width:100%;height:8px;background:rgba(255,255,255,.1);border-radius:999px;overflow:hidden}.p-progress-fill{height:100%;background:linear-gradient(90deg,#00c8ff,#0080ff);border-radius:999px}.p-pct{font-size:12px;color:#7a9bbf}.p-reward{font-size:14px;color:#ffb43c;font-weight:600}.p-btn{background:linear-gradient(135deg,#00c8ff,#0080ff);border:none;border-radius:8px;color:#fff;font-family:'Orbitron',sans-serif;font-size:12px;font-weight:700;letter-spacing:.08em;padding:11px 28px;cursor:pointer;transition:opacity .2s}.p-btn:hover{opacity:.85}
</style>
