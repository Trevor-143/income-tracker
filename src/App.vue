<template>
  <Header :totalIncome="state.totalIncome" />
  <Form @add-income="addIncome" />
</template>

<script>
import Header from './components/Header.vue'
import Form from './components/Form.vue'
import { reactive, computed } from 'vue';

export default {
  name: 'App',
  components: {
    Header,
    Form
  },
  setup() {
    const state = reactive({
      income: [ {
        value: 0
      }],
      totalIncome: computed(() => {
        let temp = 0;
        if (state.income.length > 0) {
          for (let i = 0; i < state.income.length; i++) {
            temp += state.income[i].value;
          }
        }
        return temp;
      })
    })
    const addIncome = (data) => {
      state.income = [...state.income, {
        id: Date.now(),
        desc: date.desc,
        value: date.value,
        date: data.date
      }]
    }

    return {
      state
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
