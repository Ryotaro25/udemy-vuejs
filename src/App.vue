<template>
  <div>
    <like-header> </like-header>  
    <LikeNumber></LikeNumber>
  </div>
</template>

<script>
import LikeHeader from "./componets/LikeHeader.vue";

export default {
  components: {
    LikeHeader: LikeHeader
  }
}
</script>

<style scoped>
 div {
   border: 1px solid blue;
 }
</style>



