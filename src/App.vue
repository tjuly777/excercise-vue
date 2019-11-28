<template>
  <div>
    <!--v-modelにバインディングしたデータ名を指定すると、値が連動 -->
    <input type="text" v-model="msg">
    
    <!--v-ifによるif文で、タグ単位の条件分岐が可能-->
    <p v-if="msg.length > 0">{{msg}}</p>
    <p v-else>no text.</p>
    
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
