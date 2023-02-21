<template>
  <Header :totalIncome="state.totalIncome" />
  <Form @add-income="addIncome" />
  <IncomeList :state="state" />
</template>

<script>
import Header from './components/Header.vue'
import Form from './components/Form.vue'
import { reactive, computed } from 'vue'
import IncomeList from './components/IncomeList.vue'

export default {
  name: 'App',
  components: {
    Header,
    Form,
    IncomeList
  },
  setup() {
    const state = reactive({
      income: [],
      totalIncome: computed(() => {
        let temp = 0;
        if (state.income.length > 0) {
          for (let i = 0; i < state.income.length; i++) {
            temp += state.income[i].value;
          }
        }
        return temp;
      }),
      sortedIncome: computed(() => {
        let temp =[];
        temp = state.income.sort(function (a, b) {
          return b.date - a.date;
        })
        return temp
      })
    })
    const addIncome = (data) => {
      let d = data.date.split('-')
      let newD = new Date(d[0], d[1], d[2])

      state.income = [...state.income, {
        id: Date.now(),
        desc: data.desc,
        value: parseInt(data.value),
        date: newD.getTime()
      }];
      console.log(state.income)
    }

    return {
      state,
      addIncome,
      IncomeList
    }
  }

}
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family:system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
}
body {
  background-color: #eee;
}

</style>
