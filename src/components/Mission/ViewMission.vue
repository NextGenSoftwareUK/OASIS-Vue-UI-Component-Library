<script setup lang="ts">
defineProps<{ name?: string; description?: string; status?: string; reward?: string; progress?: number }>()
const emit = defineEmits<{ close: [] }>()
</script>
<template>
  <div class="p-shell">
    <div class="p-icon">🎯</div>
    <h2 class="p-title">{{ name ?? 'Mission Details' }}</h2>
    <div class="p-status-badge" :class="`p-status--${(status ?? 'active').toLowerCase()}`">{{ status ?? 'Active' }}</div>
    <p class="p-body">{{ description ?? 'Complete objectives to advance this mission and earn rewards in the OASIS.' }}</p>
    <div class="p-reward" v-if="reward"><span class="p-reward-label">Reward</span><span class="p-reward-value">{{ reward }}</span></div>
    <div class="p-progress-wrap" v-if="progress !== undefined">
      <div class="p-progress-bar"><div class="p-progress-fill" :style="{ width: progress + '%' }"></div></div>
      <span class="p-pct">{{ progress }}% complete</span>
    </div>
    <button class="p-btn" @click="emit('close')">Close</button>
  </div>
</template>
<style scoped>
.p-shell{display:flex;flex-direction:column;align-items:center;gap:16px;padding:32px 20px;text-align:center}.p-icon{font-size:48px}.p-title{font-family:'Orbitron',sans-serif;font-size:18px;color:#fff;margin:0}.p-status-badge{font-size:11px;font-weight:700;letter-spacing:.1em;text-transform:uppercase;border-radius:999px;padding:4px 12px;border:1px solid currentColor}.p-status--active{color:#00e676}.p-status--completed{color:#ffb43c}.p-status--failed{color:#ff4444}.p-status--pending{color:#7a9bbf}.p-body{font-size:14px;color:#a8bfd8;line-height:1.6;margin:0;max-width:360px}.p-reward{background:rgba(255,180,60,.06);border:1px solid rgba(255,180,60,.2);border-radius:8px;padding:10px 16px;display:flex;gap:10px;align-items:center}.p-reward-label{font-size:11px;color:#7a9bbf;font-weight:600;letter-spacing:.08em;text-transform:uppercase}.p-reward-value{font-family:'Orbitron',sans-serif;font-size:14px;color:#ffb43c;font-weight:700}.p-progress-wrap{width:100%;max-width:300px;display:flex;flex-direction:column;gap:6px;align-items:center}.p-progress-bar{width:100%;height:8px;background:rgba(255,255,255,.1);border-radius:999px;overflow:hidden}.p-progress-fill{height:100%;background:linear-gradient(90deg,#00c8ff,#0080ff);border-radius:999px}.p-pct{font-size:12px;color:#7a9bbf}.p-btn{background:linear-gradient(135deg,#00c8ff,#0080ff);border:none;border-radius:8px;color:#fff;font-family:'Orbitron',sans-serif;font-size:12px;font-weight:700;letter-spacing:.08em;padding:11px 28px;cursor:pointer;transition:opacity .2s}.p-btn:hover{opacity:.85}
</style>
