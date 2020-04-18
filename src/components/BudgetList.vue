<template>
  <div class="budget-list-wrapp">
    <el-card :header="header" class="card">
      <div class="list-item" v-for="(item, prop) in list" :key="prop">
        <span class="budget-comment">{{ item.comment }}</span>
        <span class="budget-value">{{ item.value }}</span>
        <el-button type="danger" size="mini">Delete</el-button>
      </div>
    </el-card>
  </div>
</template>

<script>
export default {
  name: 'BudgetList',
  props: {
    list: {
      type: Object,
      default: () => ({})
    }
  },
  data: () => ({
    header: 'Budget List'
  })
}
</script>


<style scoped>
.card {
  max-width: 768px;
  margin: 0 auto;
}
.list-item {
  display: flex;
  align-items: center;
  padding: 10px 15px;
}
.budget-value {
  font-weight: bold;
  margin-left: auto;
  margin-right: 20px;
}
</style>