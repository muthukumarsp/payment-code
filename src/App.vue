<template>
  <div id="app">
    <h1> Select a Payment code </h1>

    <CategorySelect
      :paymentCodeData="paymentCodeData" 
      v-on:select-category="updateCategory"/>

    <CodeSubCodeSelect 
      v-if="codeSubCodeData.length > 0" 
      :codeSubCodeData="codeSubCodeData" 
      v-on:select-code-subcode="onCodeSubCodeSelect"/>

    <h2> Result</h2>
    <div> {{selectedCode}} </div>
  </div>
</template>

<script >
import CategorySelect from './components/CategorySelect.vue'
import CodeSubCodeSelect from './components/CodeSubCodeSelect.vue'
import PaymentCodeData from './data/payment-data.json'

export default {
  name: 'PaymentApp',
  components: {
    CategorySelect,
    CodeSubCodeSelect
  },
  data: () => ({
    paymentCodeData: PaymentCodeData,
    codeSubCodeData: [],
    selectedCode: ''
  }),
  methods: {
    updateCategory: function(category){
      this.codeSubCodeData = category.items;
    },
    onCodeSubCodeSelect: function(res) {
      this.selectedCode = res;
    },
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
