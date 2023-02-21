<template>
  <div class="income_list">
    <incomeItem v-for="data in state.sortedIncome" :key="data.id" :income="data" />
  </div>
</template>

<script>
import IncomeItem from './IncomeItem.vue';

export default {
  components: {
    IncomeItem
  },
  props: {
    state: Object
  }
}
</script>

<style scoped>
.income_list {
    margin-top: 30px;
    padding: 15px;
}

</style>