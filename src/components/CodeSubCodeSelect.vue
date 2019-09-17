<template>
    <div class="select-container">
        <select class="select-input" v-model="selected" @change="onChange"> 
          <option disabled value="">Please select a value</option>
          <option is="select-options" v-for="(group,index) in codeSubCodeData"
           :key="index" :codeItem="group"></option>
        </select>
    </div>
</template>

<script>
import SelectOptions from  './SelectOptions.vue'

export default {
  name: 'CodeSubCodeSelect',
   components: {
    SelectOptions
  },
  props: {
   codeSubCodeData: Array,
  },
   data: () => ({
    selected: '' 
  }),
  methods: {
    onChange() {
      this.$emit('select-code-subcode', this.selected);
    }
  },
  watch:{
     codeSubCodeData: {
      handler: function () { 
       this.selected = '';
       this.$emit('select-code-subcode', this.selected);
      },
      deep: true
    }
  }
}
</script>

<style lang="scss">
  @import "./styles/select-input-style.scss";
</style>