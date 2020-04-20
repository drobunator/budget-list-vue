<template>
  <div class="budget-list-wrapp">
    <el-card :header="header" class="card">
      <template v-if="isEmpty">
        <BudgetListItem
          @deleteItem="deleteItem"
          v-for="(item, prop) in list"
          :key="prop"
          v-bind:item="item"
        />
      </template>
      <el-alert :closable="false" v-else type="info" :title="emptyTitle" />
    </el-card>
  </div>
</template>

<script>
import BudgetListItem from './BudgetListItem'

export default {
  components: {
    BudgetListItem
  },
  name: 'BudgetList',
  props: {
    list: {
      type: Object,
      default: () => ({})
    }
  },
  data: () => ({
    header: 'Список доходов и расходов',
    emptyTitle: 'Список пуст'
  }),
  computed: {
    isEmpty() {
      return Object.keys(this.list).length
    }
  },
  methods: {
    deleteItem(id) {
      this.$emit('deleteItem', id)
    }
  }
}
</script>


<style scoped>
.card {
  max-width: 768px;
  margin: 0 auto;
}
</style>