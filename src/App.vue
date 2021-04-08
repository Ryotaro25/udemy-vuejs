<template>
  <div class="main">
    <button @click="myAnimation ='slide'">Slide</button>
    <button @click="myAnimation='fade'">fade</button>

    <button @click="show=!show">きりかえ</button>
    <br><br>
    <transition
    :css="false"
    @before-enter="beforeEnter" 
    @enter="enter" 
    @leave="leave" 
    >
      <div class="circle" v-if="show"></div>
    </transition>
    
    <p>{{myAnimation}}</p>
    <br>
    <button @click="myComponent ='ComponentA'">ComponentA</button>
    <button @click="myComponent='ComponentB'">ComponentB</button>
    <transition name="fade" mode="out-in">
      <component :is="myComponent"></component>
    </transition>
    
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
import ComponentA from "./components/ComponentA.vue";
import ComponentB from "./components/ComponentB.vue";

export default {
  components: {
    ComponentA,
    ComponentB
  },
  data() {
    return {
      show: true,
      myAnimation: "slide",
      myComponent: "ComponentA"
    };
  },
  methods: {
    beforeEnter(el) {
      
    },
    enter(el, done) {
     let scale = 0;
     const interval = setInterval(() => {
       el.style.transform = 'scale($(scale))'
       scale += 0.1
       if (scale > 1) {
         clearInterval(interval);
         done();
       }
     }, 200);
    },
    afterEnter(el) {

    },
    enterCancelled(el) {

    },
    beforeLeave(el) {

    },
    leave(el, done) {
      let scale = 1;
      const interval = setInterval(() => {
      el.style.transform = 'scale($(scale))'
      scale -= 0.1
      if (scale < 0) {
       clearInterval(interval);
         done();
       }
     }, 200);
    },
    afterLeave(el) {

    },
    leaveCancelled(el) {

    }
  }
};
</script>

<style scoped>
  .circle {
    width: 200px;
    height: 200px;
    margin: auto;
    background-color: deeppink;
    border-radius: 100px;
  }

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