<template>
  <form @submit.prevent="formHandler">
    <input type="text" placeholder="Describe" v-model="formData.desc">
    <input type="number" placeholder="value" v-model="formData.value" >
    <input type="date" placeholder="Date" v-model="formData.date" >
    <input type="submit" value="Submit">
  </form>
</template>

<script>
import { reactive } from 'vue'

export default {
    props: {
        state: Object
    },
    setup( props, { emit } ) {
        const formData = reactive({
            desc: null,
            value: null,
            date: null
        });
        const formHandler = () => {
            // console.log(formData)
            emit('add-income', {
                desc: formData.desc,
                value: formData.value,
                date: formData.date
            })
            formData.desc = null, 
            formData.value = null, 
            formData.date = null 

        }
        return {
            formHandler,
            formData
        }
    }


}
</script>

<style>
form {
    display: flex;
    justify-content: center;
    margin-top: 30px;
  }
  form input {
    color: #888;
    border: none;
    outline: none;
    font-size: 20px;
  }
  form input::placeholder {
    color: #AAA;
  }
  form input:not([type="submit"]) {
    display: block;
    background: #FFF;
    border: none;
    outline: none;
    padding: 10px 15px;
  }
  form input[type="submit"] {
    display: block;
    background: none;
    border: none;
    outline: none;
    color: #FFF;
    font-weight: 500;
    text-shadow: 0px 1px 3px rgba(0, 0, 0, 0.2);
    padding: 5px 15px;
    background-color: #7a0404;
    cursor: pointer;
  }
  form input:first-of-type {
    border-radius: 15px 0px 0px 15px;
  }
  form input:last-of-type {
    border-radius: 0px 15px 15px 0px;
  }
</style>