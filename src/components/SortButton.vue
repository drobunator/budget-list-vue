<template>
  <el-card class="button-block">
    <el-button @click="onSortBtn('INCOME')" type="success">Доходы</el-button>
    <el-button @click="onSortBtn('')" type="primary">Все средства</el-button>
    <el-button @click="onSortBtn('OUTCOME')" type="danger">Рассходы</el-button>
  </el-card>
</template>

<script>
export default {
  name: 'SortButton',
  methods: {
    onSortBtn(value) {
      this.$emit('sortList', value)
    }
  }
}
</script>

<style scoped>
.button-block {
  max-width: 768px;
  margin: 0 auto 30px;
}
</style>