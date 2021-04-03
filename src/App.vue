<template>
  <div>
    <like-header header-text="hello">
      <template v-slot:title>
        <h2>こんにちは</h2>
      </template>
      <template v-slot:number>
        <p>{{number}}</p>
      </template>
    </like-header>  
    <LikeNumber v-bind:total-number='number' @my-click="incrementNumber"></LikeNumber>
    <LikeNumber :totalNumber='number'> </LikeNumber>
  </div>
</template>

<script>
import LikeHeader from "./componets/LikeHeader.vue";

export default {
  data() {
    return {
      number: 14
    };
  },
  components: {
    LikeHeader
  },
  methods: {
    incrementNumber(value) {
      this.number = value;
    }
  }
}
</script>

<style>
 div {
   border: 1px solid blue;
 }

 h1 {
   color: red;
 }
</style>



