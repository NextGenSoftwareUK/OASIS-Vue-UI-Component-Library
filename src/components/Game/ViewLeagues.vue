<script setup lang="ts">
const emit = defineEmits<{ close: [] }>()
const leagues = [
  { name: 'Bronze League', members: 1240, minKarma: 0, icon: '🥉' },
  { name: 'Silver League', members: 560, minKarma: 500, icon: '🥈' },
  { name: 'Gold League', members: 210, minKarma: 2000, icon: '🥇' },
  { name: 'Diamond League', members: 42, minKarma: 10000, icon: '💎' },
]
</script>
<template>
  <div class="p-shell">
    <h2 class="p-title">🏅 Leagues</h2>
    <div class="p-list">
      <div v-for="l in leagues" :key="l.name" class="p-item">
        <span class="p-item-icon">{{ l.icon }}</span>
        <div class="p-item-info"><span class="p-item-name">{{ l.name }}</span><span class="p-item-desc">{{ l.members }} members · Min Karma {{ l.minKarma }}</span></div>
        <button class="p-join-btn">Join</button>
      </div>
    </div>
    <button class="p-btn" @click="emit('close')">Close</button>
  </div>
</template>
<style scoped>
.p-shell{display:flex;flex-direction:column;gap:18px;padding:24px 20px}.p-title{font-family:'Orbitron',sans-serif;font-size:18px;color:#fff;margin:0}.p-list{display:flex;flex-direction:column;gap:10px}.p-item{display:flex;align-items:center;gap:14px;background:rgba(255,255,255,.04);border:1px solid rgba(0,200,255,.15);border-radius:10px;padding:14px}.p-item-icon{font-size:28px;flex-shrink:0}.p-item-info{display:flex;flex-direction:column;gap:3px;flex:1}.p-item-name{font-family:'Orbitron',sans-serif;font-size:13px;color:#fff;font-weight:700}.p-item-desc{font-size:12px;color:#7a9bbf}.p-join-btn{background:rgba(0,200,255,.12);border:1px solid rgba(0,200,255,.3);border-radius:6px;color:#00c8ff;font-family:'Orbitron',sans-serif;font-size:10px;font-weight:700;letter-spacing:.06em;padding:6px 14px;cursor:pointer;transition:background .2s}.p-join-btn:hover{background:rgba(0,200,255,.2)}.p-btn{align-self:flex-end;background:linear-gradient(135deg,#00c8ff,#0080ff);border:none;border-radius:8px;color:#fff;font-family:'Orbitron',sans-serif;font-size:12px;font-weight:700;letter-spacing:.08em;padding:10px 24px;cursor:pointer;transition:opacity .2s}.p-btn:hover{opacity:.85}
</style>
