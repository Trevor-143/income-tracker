<template>
    <header>
        <h1>Income Tracker</h1>
        <div class="total-income">shs. {{ totalIncome }}</div>
    </header>
</template>

<script>

export default {
    name: 'Header',
    props: {
        totalIncome: Number
    }

}

</script>

<style scoped>
header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 15px 30px;
    background-color: #181818;
    border-bottom: 5px solid #7a0404;

}
header h1 {
    color: #eee;
    font-size: 28px;

}
header .total-income {
    font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
    background: #7a0404;
    color: #fff;
    font-size: 20px;
    font-weight: 900;
    padding: 5px 10px;
    min-width: 100px;
    text-align: center;
    border-radius: 8px;

}
</style>