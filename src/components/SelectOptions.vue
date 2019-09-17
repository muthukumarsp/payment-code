<template>
    <option v-if="!codeItem.subCodeList" :value={...codeItem}>
       {{codeItem.code + ":" + codeItem.desc}}
    </option>
    <optgroup v-else :label="codeItem.code + codeItem.desc">
         <option :key="index" :value={code:codeItem.code,desc:codeItem.desc,...option} 
             v-for="(option,index) in codeItem.subCodeList">
            {{ option.subCode + ":" + option.subCodeDesc }}
        </option>
    </optgroup>
</template>

<script>
export default {
  props: [
   'codeItem'
 ]
}
</script> 