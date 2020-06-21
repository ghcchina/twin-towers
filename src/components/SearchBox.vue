<template>
  <div>
    <form @submit="doSearch">
      <input type="text" v-model="text" name="query" placeholder="try it...">
      <input type="submit" value="Search" class="btn">
    </form>
  </div>
</template>

<script>
export default {
  name: "SearchBox",
  data() {
    return {
      text: ''
    }
  },
  methods: {
    doSearch(e) {
      // suspend default behavior, otherwise the form submit will be fired
      e.preventDefault();

      const searchQuery = {
        q: this.text
      }
      
      // Send up
      this.$emit('do-search', searchQuery);

      this.text = '';
    }
  }
}
</script>

<style scoped>
  form {
    display: flex;
  }

  input[type="text"] {
    flex: 10;
    padding: 5px;
  }

  input[type="submit"] {
    flex: 2;
  }

  .btn {
    display: inline-block;
    border: none;
    background: #555;
    color: #fff;
    padding: 7px 20px;
    cursor: pointer;
  }

  .btn:hover {
    background: #666;
  }
</style>