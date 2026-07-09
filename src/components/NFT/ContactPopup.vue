<script setup lang="ts">
const emit = defineEmits<{ close: [] }>()
const contacts = [
  { name: 'Alice Wonderland', country: 'UK', group: 'Friends' },
  { name: 'Bob Builder', country: 'USA', group: 'Colleagues' },
  { name: 'Charlie Brown', country: 'Canada', group: 'Friends' },
  { name: 'Diana Prince', country: 'Greece', group: 'Family' },
]
const groups = ['Friends', 'Family', 'Colleagues', 'My List 1', 'My List 2']
</script>
<template>
  <div class="p-shell">
    <h2 class="p-title">👥 Contacts</h2>
    <div class="p-group-bar">
      <button v-for="g in groups" :key="g" class="p-group-btn">{{ g }}</button>
    </div>
    <div class="p-table-wrap">
      <table class="p-table">
        <thead><tr><th>Name</th><th>Country</th><th>Group</th></tr></thead>
        <tbody>
          <tr v-for="c in contacts" :key="c.name">
            <td>{{ c.name }}</td><td>{{ c.country }}</td><td>{{ c.group }}</td>
          </tr>
        </tbody>
      </table>
    </div>
    <div class="p-foot-btns">
      <button class="p-foot-btn">Find Avatar</button>
      <button class="p-foot-btn">Create List</button>
    </div>
    <button class="p-btn" @click="emit('close')">Close</button>
  </div>
</template>
<style scoped>
.p-shell{display:flex;flex-direction:column;gap:16px;padding:24px 20px}.p-title{font-family:'Orbitron',sans-serif;font-size:18px;color:#fff;margin:0}.p-group-bar{display:flex;gap:8px;flex-wrap:wrap}.p-group-btn{background:rgba(0,200,255,.08);border:1px solid rgba(0,200,255,.2);border-radius:6px;color:#00c8ff;font-size:12px;font-weight:600;padding:6px 14px;cursor:pointer;transition:background .2s}.p-group-btn:hover{background:rgba(0,200,255,.16)}.p-table-wrap{overflow-x:auto;border-radius:10px;border:1px solid rgba(0,200,255,.15)}.p-table{width:100%;border-collapse:collapse;font-size:13px}.p-table th{background:rgba(0,200,255,.08);color:#00c8ff;font-family:'Orbitron',sans-serif;font-size:11px;font-weight:700;letter-spacing:.06em;padding:10px 12px;text-align:left}.p-table td{color:#c8dff0;padding:9px 12px;border-top:1px solid rgba(255,255,255,.05)}.p-table tr:hover td{background:rgba(0,200,255,.04)}.p-foot-btns{display:flex;gap:10px;justify-content:flex-end}.p-foot-btn{background:rgba(0,200,255,.08);border:1px solid rgba(0,200,255,.2);border-radius:6px;color:#00c8ff;font-size:12px;font-weight:600;padding:7px 16px;cursor:pointer}.p-btn{align-self:flex-end;background:linear-gradient(135deg,#00c8ff,#0080ff);border:none;border-radius:8px;color:#fff;font-family:'Orbitron',sans-serif;font-size:12px;font-weight:700;letter-spacing:.08em;padding:10px 24px;cursor:pointer;transition:opacity .2s}.p-btn:hover{opacity:.85}
</style>
