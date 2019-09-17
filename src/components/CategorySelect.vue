<template>
<div class="select-container">
  <select class="select-input" v-model="selected" @change="onChange">
  <option v-for="(option,index) in paymentCodeData" v-bind:value="option" :key="index">
    {{ option.category}}
  </option>
</select>
</div>
</template>

<script>
export default {
  name: 'CategorySelect',
  props: {
   paymentCodeData: Array,
  },
   data: () => ({
    selected: '',
  }),
  methods: {
    onChange() {
      this.$emit('select-category', this.selected);
    }
  }
}
</script>

<style lang="scss">
  @import "./styles/select-input-style.scss";
</style>