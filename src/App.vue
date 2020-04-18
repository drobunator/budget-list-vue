<template>
  <div id="app">
    <TotalBalance :total="totalBalance" />
    <Form />
    <BudgetList :list="list" @deleteItem="onDeleteItem" />
  </div>
</template>

<script>
import BudgetList from './components/BudgetList'
import TotalBalance from './components/TotalBalance'
import Form from './components/Form'

export default {
  name: 'App',
  components: {
    BudgetList,
    TotalBalance,
    Form
  },
  data: () => ({
    list: {
      1: {
        type: 'INCOME',
        value: 100,
        comment: 'Какой-то доход',
        id: 1
      },
      2: {
        type: 'OUTCOME',
        value: -50,
        comment: 'Какой-то расхоход',
        id: 2
      }
    }
  }),
  computed: {
    totalBalance() {
      return Object.values(this.list).reduce((acc, item) => {
        return acc + item.value
      }, 0)
    }
  },
  methods: {
    onDeleteItem(id) {
      console.log(id)
      this.$delete(this.list, id)
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
