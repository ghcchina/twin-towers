<template>
  <div>
    <Request v-bind:header="req.header" v-bind:body="req.body" 
      v-on:clear-header="$emit('clear-req-header')" 
      v-on:clear-body="$emit('clear-req-body')" />
  </div>    
</template>

<script>
import Request from './Request.vue';

export default {
  name: "Sibling",
  components: {
    Request
  },
  props: ["req"]   
}
</script>

<style lang="stylus" scoped>

</style>