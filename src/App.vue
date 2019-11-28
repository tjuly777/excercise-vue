<template>
  <div>
    <p>{{msg}}</p>
    <input type="text" v-model="msg">
  </div>
</template>

<script>
  export default {
    data() {
      return {
        msg: "It's a Sample."
      }
    }
  }
</script>
