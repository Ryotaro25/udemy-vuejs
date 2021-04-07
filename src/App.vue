<template>
  <div class="main">
    <button @click="myAnimation ='slide'">Slide</button>
    <button @click="myAnimation='fade'">fade</button>

    <button @click="show=!show">きりかえ</button>
    <p>{{myAnimation}}</p>
    <transition name="fade" mode="out-in">
      <p v-if="show" key="bye">さようなら</p>
      <p v-else key="hello">こんにちは</p>
    </transition>

    <transition :name="myAnimation"  appear>
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
    transition: opacity 0.5s;
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