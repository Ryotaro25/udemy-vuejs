<template>
  <div class="main">
    <button @click="show=!show">きりかえ</button>
    <transition name="fade">
      <p v-if="show">hello</p>
    </transition>
    <transition name="slide" type="animation">
    <p v-if="show">bye</p>
    
    </transition>
  </div>
</template>

<script>
export default {
  data() {
    return {
      show: true
    };
  }
};
</script>

<style scoped>
  .fade-enter {
    opacity: 0;
  }
  .fade-enter-active {
    transition: opacity 1s;
  }
  .fade-enter-to {
    opacity: 1;
  }
  .fade-leave {
    opacity: 1;
  }
  .fade-leave-active {
    transition: opacity 1s;
  }
  .fade-leave-to {
    opacity: 0;
  }

  .slide-enter,
  .slide-leave-to {
    opacity: 0;
  }
  .slide-enter-active {
    animation: slide-in 0.5s;
    opacity: 0.5s;
  }
  
  .slide-leave-active {
    animation: slide-in 0.5s reverse;
    opacity: 0.5s;
  }


  @keyframes slide-in {
    from {
      transform: translateX(100px);
    }
    to {
      transform: translateX(0);
    }
  }
  
  .main {
    width: 70%;
    margin: auto;
    padding-top: 5rem;
    text-align: center;
  }
</style>