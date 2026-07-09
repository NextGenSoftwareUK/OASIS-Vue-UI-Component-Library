<script setup lang="ts">
const emit = defineEmits<{ close: [] }>()
const achievements = [
  { icon: '⭐', name: 'First Steps', desc: 'Complete your first quest', earned: true },
  { icon: '🏆', name: 'Champion', desc: 'Win 10 tournaments', earned: true },
  { icon: '🌍', name: 'World Explorer', desc: 'Visit 50 locations in Our World', earned: false },
  { icon: '💎', name: 'Legendary', desc: 'Reach Karma level 1000', earned: false },
]
</script>
<template>
  <div class="p-shell">
    <h2 class="p-title">🏆 Achievements</h2>
    <div class="p-list">
      <div v-for="a in achievements" :key="a.name" class="p-item" :class="{ 'p-item--locked': !a.earned }">
        <span class="p-item-icon">{{ a.icon }}</span>
        <div class="p-item-info"><span class="p-item-name">{{ a.name }}</span><span class="p-item-desc">{{ a.desc }}</span></div>
        <span class="p-item-status">{{ a.earned ? '✅' : '🔒' }}</span>
      </div>
    </div>
    <button class="p-btn" @click="emit('close')">Close</button>
  </div>
</template>
<style scoped>
.p-shell{display:flex;flex-direction:column;gap:18px;padding:24px 20px}.p-title{font-family:'Orbitron',sans-serif;font-size:18px;color:#fff;margin:0}.p-list{display:flex;flex-direction:column;gap:10px}.p-item{display:flex;align-items:center;gap:14px;background:rgba(255,255,255,.04);border:1px solid rgba(0,200,255,.15);border-radius:10px;padding:14px}.p-item--locked{opacity:.5}.p-item-icon{font-size:28px;flex-shrink:0}.p-item-info{display:flex;flex-direction:column;gap:3px;flex:1}.p-item-name{font-family:'Orbitron',sans-serif;font-size:13px;color:#fff;font-weight:700}.p-item-desc{font-size:12px;color:#7a9bbf}.p-item-status{font-size:20px}.p-btn{align-self:flex-end;background:linear-gradient(135deg,#00c8ff,#0080ff);border:none;border-radius:8px;color:#fff;font-family:'Orbitron',sans-serif;font-size:12px;font-weight:700;letter-spacing:.08em;padding:10px 24px;cursor:pointer;transition:opacity .2s}.p-btn:hover{opacity:.85}
</style>
