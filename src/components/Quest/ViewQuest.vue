<script setup lang="ts">
defineProps<{ name?: string; description?: string; difficulty?: string; reward?: string; xp?: number }>()
const emit = defineEmits<{ close: []; accept: [] }>()
</script>
<template>
  <div class="p-shell">
    <div class="p-icon">⚔️</div>
    <h2 class="p-title">{{ name ?? 'Quest Details' }}</h2>
    <div class="p-diff-badge" v-if="difficulty" :class="`p-diff--${difficulty.toLowerCase()}`">{{ difficulty }}</div>
    <p class="p-body">{{ description ?? 'Venture forth into the OASIS and complete this quest to earn rewards and karma.' }}</p>
    <div class="p-rewards">
      <div class="p-reward" v-if="reward"><span class="p-reward-label">Reward</span><span class="p-reward-value">{{ reward }}</span></div>
      <div class="p-reward" v-if="xp !== undefined"><span class="p-reward-label">XP</span><span class="p-reward-value">+{{ xp }}</span></div>
    </div>
    <div class="p-actions">
      <button class="p-btn-cancel" @click="emit('close')">Close</button>
      <button class="p-btn" @click="emit('accept')">Accept Quest</button>
    </div>
  </div>
</template>
<style scoped>
.p-shell{display:flex;flex-direction:column;align-items:center;gap:16px;padding:32px 20px;text-align:center}.p-icon{font-size:48px}.p-title{font-family:'Orbitron',sans-serif;font-size:18px;color:#fff;margin:0}.p-diff-badge{font-size:11px;font-weight:700;letter-spacing:.1em;text-transform:uppercase;border-radius:999px;padding:4px 12px;border:1px solid currentColor}.p-diff--easy{color:#00e676}.p-diff--medium{color:#ffb43c}.p-diff--hard{color:#ff7744}.p-diff--legendary{color:#b87fff}.p-body{font-size:14px;color:#a8bfd8;line-height:1.6;margin:0;max-width:360px}.p-rewards{display:flex;gap:12px}.p-reward{background:rgba(255,180,60,.06);border:1px solid rgba(255,180,60,.2);border-radius:8px;padding:10px 16px;display:flex;flex-direction:column;gap:4px;align-items:center}.p-reward-label{font-size:11px;color:#7a9bbf;font-weight:600;letter-spacing:.08em;text-transform:uppercase}.p-reward-value{font-family:'Orbitron',sans-serif;font-size:15px;color:#ffb43c;font-weight:700}.p-actions{display:flex;gap:12px}.p-btn{background:linear-gradient(135deg,#00c8ff,#0080ff);border:none;border-radius:8px;color:#fff;font-family:'Orbitron',sans-serif;font-size:12px;font-weight:700;letter-spacing:.08em;padding:11px 28px;cursor:pointer;transition:opacity .2s}.p-btn:hover{opacity:.85}.p-btn-cancel{background:transparent;border:1px solid rgba(0,200,255,.3);border-radius:8px;color:#00c8ff;font-family:'Orbitron',sans-serif;font-size:12px;font-weight:700;letter-spacing:.08em;padding:11px 28px;cursor:pointer}
</style>
