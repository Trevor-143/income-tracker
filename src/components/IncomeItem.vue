
<template>
    <div class="income-item">
      <div class="removeItem">x</div>
      <div class="desc">{{ income.desc }}</div>
      <div class="price">${{ income.value }}</div>
      <div class="date">{{ formattedDate }}</div>
    </div>
  </template>
  
  <script>
  export default {
    name: 'IncomeItem',
    props: {
      income: Object
    },
    computed: {
      formattedDate () {
        let date = new Date(this.income.date)
        let month = date.getMonth()
        let day = date.getDate()
        let year = date.getFullYear()
        return month + '/' + day + '/' + year
      }
    }
  }
  </script>
  
  <style scoped>
  .income-item {
    position: relative;
    display: flex;
    padding: 15px 15px 15px 0px;
    background-color: #fff;
    border-radius: 99px;
    max-width: 600px;
    margin: 0 auto 30px;
  }
  .removeItem {
    color: #7a0404;
    font-weight: 600;
    font-size: 20px;
    line-height: 1;
    text-align: center;
    margin: 0 15px;
  }
  .desc {
    color: #666;
    flex: 1 1 100%;
    font-size: 20px;
  }
  .price {
    color: #666;
    min-width: 100px;
    font-size: 20px;
  }
  .date {
    color: #666;
    text-align: right;
    font-size: 20px;
  }
  </style>