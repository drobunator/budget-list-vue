<template>
  <div class="list-item">
    <span class="budget-icon">
      <i :class="setIconClass"></i>
    </span>
    <span class="budget-comment">{{ item.comment }}</span>
    <span class="budget-value">{{ item.value }}</span>
    <el-button type="danger" size="mini" @click="deleteItem(item.id)">Удалить</el-button>
  </div>
</template>

<script>
export default {
  name: 'BudgetListItem',
  props: {
    item: {
      type: Object,
      default: () => ({})
    }
  },
  methods: {
    deleteItem(id) {
      const isConfirm = confirm('Вы уверены что хотите удалить?')
      if (isConfirm) {
        this.$emit('deleteItem', id)
      }
    }
  },
  computed: {
    setIconClass() {
      return this.item.type === 'INCOME' ? 'el-icon-top' : 'el-icon-bottom'
    }
  }
}
</script>


<style scoped>
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
.budget-icon {
  margin-right: 15px;
}
</style>