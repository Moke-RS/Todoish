<template>
  <div class="header">
      <span><h1>{{ appName }}</h1> - a (kind of) To Do tool</span>
  </div>
</template>

<style scoped>
  .header {
    position: relative;
    top: 0;
    left: 0;
    width: 100%;
    border-bottom: 1px solid black;
  }

  h1 {
    display: inline-block;
    margin: 10px 0px 5px 20px;
  }
</style>


<script>
export default {
  props: ['appName']
}
</script>

