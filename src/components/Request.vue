<template>
  <div>
    <p class="section">
      {{header}}
      <button v-on:click="$emit('clear-header')" class="del">x</button>
    </p>
    <p class="section">
      {{body}}
      <button v-on:click="$emit('clear-body')" class="del">x</button>
    </p>
  </div>
</template>

<script>
export default {
  name: "Request",
  props: ["header", "body"]
}
</script>

<style scoped>
  .section {
    background: #f4f4f4;
    padding: 10px;
    border-bottom: 1px #ccc dotted;
  }

  .del {
    background: #ff0000;
    color: #fff;
    border: none;
    padding: 5px 9px;
    border-radius: 50%;
    cursor: pointer;
    float: right;
  }
</style>