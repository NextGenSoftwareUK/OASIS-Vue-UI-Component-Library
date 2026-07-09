<script setup lang="ts">
const emit = defineEmits<{ close: [] }>()
const entries = [
  { date: '2024-01-10', action: 'Completed Quest', amount: '+50', total: '550' },
  { date: '2024-01-08', action: 'Helped Avatar', amount: '+20', total: '500' },
  { date: '2024-01-05', action: 'Joined League', amount: '+30', total: '480' },
  { date: '2024-01-01', action: 'Welcome bonus', amount: '+100', total: '100' },
]
</script>
<template>
  <div class="p-shell">
    <h2 class="p-title">⭐ Karma Log</h2>
    <div class="p-table-wrap">
      <table class="p-table">
        <thead><tr><th>Date</th><th>Action</th><th>Amount</th><th>Total</th></tr></thead>
        <tbody>
          <tr v-for="(e, i) in entries" :key="i">
            <td>{{ e.date }}</td><td>{{ e.action }}</td>
            <td :class="e.amount.startsWith('+') ? 'pos' : 'neg'">{{ e.amount }}</td>
            <td>{{ e.total }}</td>
          </tr>
        </tbody>
      </table>
    </div>
    <button class="p-btn" @click="emit('close')">Close</button>
  </div>
</template>
<style scoped>
.p-shell{display:flex;flex-direction:column;gap:18px;padding:24px 20px}.p-title{font-family:'Orbitron',sans-serif;font-size:18px;color:#fff;margin:0}.p-table-wrap{overflow-x:auto;border-radius:10px;border:1px solid rgba(0,200,255,.15)}.p-table{width:100%;border-collapse:collapse;font-size:13px}.p-table th{background:rgba(0,200,255,.08);color:#00c8ff;font-family:'Orbitron',sans-serif;font-size:11px;font-weight:700;letter-spacing:.06em;padding:10px 12px;text-align:left}.p-table td{color:#c8dff0;padding:9px 12px;border-top:1px solid rgba(255,255,255,.05)}.p-table tr:hover td{background:rgba(0,200,255,.04)}.pos{color:#00e676;font-weight:700}.neg{color:#ff4444;font-weight:700}.p-btn{align-self:flex-end;background:linear-gradient(135deg,#00c8ff,#0080ff);border:none;border-radius:8px;color:#fff;font-family:'Orbitron',sans-serif;font-size:12px;font-weight:700;letter-spacing:.08em;padding:10px 24px;cursor:pointer;transition:opacity .2s}.p-btn:hover{opacity:.85}
</style>
