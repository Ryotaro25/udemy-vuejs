<template>
  <div>
    <like-header> </like-header>  
    <p>いいね{{ number }}</p>
    <LikeNumber v-bind:number='number'></LikeNumber>
    <LikeNumber :number='number'> </LikeNumber>
  </div>
</template>

<script>
import LikeHeader from "./componets/LikeHeader.vue";

export default {
  data() {
    return {
      number: 10
    }
  },
  components: {
    LikeHeader: LikeHeader
  }
}
</script>

<style>
 div {
   border: 1px solid blue;
 }
</style>



