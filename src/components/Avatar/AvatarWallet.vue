<script setup lang="ts">
interface WalletRow { date: string; note: string; fromAvatar: string; fromWallet: string; token: string; amount: string; balance: string; provider: string; type: string }
const emit = defineEmits<{ close: [] }>()
const rows: WalletRow[] = [
  { date: '2024-01-01', note: 'Initial deposit', fromAvatar: 'System', fromWallet: 'Genesis', token: 'KARMA', amount: '+500', balance: '500', provider: 'Holochain', type: 'Credit' },
  { date: '2024-01-15', note: 'Quest reward', fromAvatar: 'QuestMaster', fromWallet: '0xabc...', token: 'SEEDS', amount: '+100', balance: '600', provider: 'Ethereum', type: 'Credit' },
]
</script>
<template>
  <div class="p-shell">
    <h2 class="p-title">💳 Avatar Wallet</h2>
    <div class="p-table-wrap">
      <table class="p-table">
        <thead>
          <tr><th>Date</th><th>Note</th><th>From Avatar</th><th>From Wallet</th><th>Token</th><th>Amount</th><th>Balance</th><th>Provider</th><th>Type</th></tr>
        </thead>
        <tbody>
          <tr v-for="(r, i) in rows" :key="i">
            <td>{{ r.date }}</td><td>{{ r.note }}</td><td>{{ r.fromAvatar }}</td><td>{{ r.fromWallet }}</td><td>{{ r.token }}</td><td>{{ r.amount }}</td><td>{{ r.balance }}</td><td>{{ r.provider }}</td><td>{{ r.type }}</td>
          </tr>
        </tbody>
      </table>
    </div>
    <button class="p-btn" @click="emit('close')">Close</button>
  </div>
</template>
<style scoped>
.p-shell{display:flex;flex-direction:column;gap:18px;padding:24px 20px}.p-title{font-family:'Orbitron',sans-serif;font-size:18px;color:#fff;margin:0}.p-table-wrap{overflow-x:auto;border-radius:10px;border:1px solid rgba(0,200,255,.15)}.p-table{width:100%;border-collapse:collapse;font-size:13px}.p-table th{background:rgba(0,200,255,.08);color:#00c8ff;font-family:'Orbitron',sans-serif;font-size:11px;font-weight:700;letter-spacing:.06em;padding:10px 12px;text-align:left;white-space:nowrap}.p-table td{color:#c8dff0;padding:9px 12px;border-top:1px solid rgba(255,255,255,.05)}.p-table tr:hover td{background:rgba(0,200,255,.04)}.p-btn{align-self:flex-end;background:linear-gradient(135deg,#00c8ff,#0080ff);border:none;border-radius:8px;color:#fff;font-family:'Orbitron',sans-serif;font-size:12px;font-weight:700;letter-spacing:.08em;padding:10px 24px;cursor:pointer;transition:opacity .2s}.p-btn:hover{opacity:.85}
</style>
