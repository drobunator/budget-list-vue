<template>
  <div id="app">
    <TotalBalance :style="{color: onTotalColor}" :total="totalBalance" />
    <Form @submitForm="onSubmit" />
    <SotButton @sortList="onSortList" />
    <BudgetList :list="listData" @deleteItem="onDeleteItem" />
  </div>
</template>

<script>
import BudgetList from './components/BudgetList'
import TotalBalance from './components/TotalBalance'
import Form from './components/Form'
import SotButton from './components/SortButton'

export default {
  name: 'App',
  components: {
    BudgetList,
    TotalBalance,
    Form,
    SotButton
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
        value: -550,
        comment: 'Какой-то расхоход',
        id: 2
      },
      4: {
        type: 'INCOME',
        value: 500,
        comment: 'Какой-то доход',
        id: 4
      },
      5: {
        type: 'OUTCOME',
        value: -50,
        comment: 'Какой-то расхоход',
        id: 5
      },
      6: {
        type: 'INCOME',
        value: 150,
        comment: 'Какой-то расхоход',
        id: 6
      }
    },
    sortValue: ''
  }),
  computed: {
    totalBalance() {
      return Object.values(this.list).reduce((acc, item) => {
        return acc + item.value
      }, 0)
    },
    onTotalColor() {
      return this.totalBalance > 0
        ? 'green'
        : this.totalBalance < 0
        ? 'red'
        : 'black'
    },
    listData() {
      if (!this.sortValue) return this.list
      return Object.values(this.list)
        .filter(item => {
          return item.type === this.sortValue
        })
        .reduce((acc, el) => {
          acc[el.id] = el
          return acc
        }, {})
    }
  },
  methods: {
    onDeleteItem(id) {
      this.$delete(this.list, id)
    },
    onSubmit(data) {
      this.$set(this.list, data.id, data)
    },
    onSortList(value) {
      this.sortValue = value
      console.log(this.totalBalance)
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
  margin-top: 20px;
}
</style>
