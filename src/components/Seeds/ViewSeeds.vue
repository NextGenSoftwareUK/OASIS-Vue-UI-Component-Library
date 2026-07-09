<script setup lang="ts">
defineProps<{ balance?: number; username?: string; impact?: string }>()
const emit = defineEmits<{ close: [] }>()
const transactions = [
  { date: '2024-01-10', description: 'Quest reward', amount: '+50' },
  { date: '2024-01-08', description: 'Donation to Earth Regen', amount: '-20' },
  { date: '2024-01-05', description: 'Welcome seeds', amount: '+100' },
]
</script>
<template>
  <div class="p-shell">
    <div class="p-icon">🌱</div>
    <h2 class="p-title">{{ username ?? 'My' }} Seeds</h2>
    <div class="p-balance">
      <span class="p-balance-label">Balance</span>
      <span class="p-balance-value">{{ (balance ?? 0).toLocaleString() }} SEEDS</span>
    </div>
    <div class="p-table-wrap">
      <table class="p-table">
        <thead><tr><th>Date</th><th>Description</th><th>Amount</th></tr></thead>
        <tbody>
          <tr v-for="(t, i) in transactions" :key="i">
            <td>{{ t.date }}</td><td>{{ t.description }}</td>
            <td :class="t.amount.startsWith('+') ? 'pos' : 'neg'">{{ t.amount }}</td>
          </tr>
        </tbody>
      </table>
    </div>
    <button class="p-btn" @click="emit('close')">Close</button>
  </div>
</template>
<style scoped>
.p-shell{display:flex;flex-direction:column;gap:18px;padding:24px 20px;align-items:center;text-align:center}.p-icon{font-size:44px}.p-title{font-family:'Orbitron',sans-serif;font-size:18px;color:#fff;margin:0}.p-balance{background:rgba(0,200,255,.06);border:1px solid rgba(0,200,255,.2);border-radius:10px;padding:14px 24px;display:flex;flex-direction:column;gap:6px}.p-balance-label{font-size:11px;color:#7a9bbf;font-weight:600;letter-spacing:.1em;text-transform:uppercase}.p-balance-value{font-family:'Orbitron',sans-serif;font-size:24px;color:#00e676;font-weight:700}.p-table-wrap{width:100%;overflow-x:auto;border-radius:10px;border:1px solid rgba(0,200,255,.15)}.p-table{width:100%;border-collapse:collapse;font-size:13px}.p-table th{background:rgba(0,200,255,.08);color:#00c8ff;font-family:'Orbitron',sans-serif;font-size:11px;font-weight:700;letter-spacing:.06em;padding:10px 12px;text-align:left}.p-table td{color:#c8dff0;padding:9px 12px;border-top:1px solid rgba(255,255,255,.05)}.pos{color:#00e676;font-weight:700}.neg{color:#ff4444;font-weight:700}.p-btn{background:linear-gradient(135deg,#00c8ff,#0080ff);border:none;border-radius:8px;color:#fff;font-family:'Orbitron',sans-serif;font-size:12px;font-weight:700;letter-spacing:.08em;padding:11px 28px;cursor:pointer;transition:opacity .2s}.p-btn:hover{opacity:.85}
</style>
