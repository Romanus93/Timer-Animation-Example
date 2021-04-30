<template>
<div>
  <div class="animation-box">
    <div>
      <div class="box1 image-background">
        <div class="image-egg flex" v-show="Z">
          <img class="slight-shaking" src="../assets/white-egg.svg" alt="">
        </div>
      </div>
    </div>
  </div>
  <div class="animation-box">
    <div class="box1" v-show="A">
      <div class="image-egg flex">
        <img class="medium-shaking" src="../assets/craked-egg.svg" alt="">
      </div>
    </div>
  </div>
  <div class="animation-box">
    <div class="box1" v-show="B">
      <div class="image-egg flex">
        <img class="strong-shaking" src="../assets/craked-egg.svg" alt="">
      </div>
    </div>
  </div>
  <div class="animation-box">
    <div class="box1" v-show="C">
      <div class="image-egg flex position-wrapper">
        <img class="strong-shaking position" src="../assets/craked-egg.svg" alt="">
        <img class="stronger-shaking position opacity" src="../assets/craked-egg.svg" alt="">
      </div>
    </div>
  </div>
  <div>
    <button @click="showA(true)"> 1.Lorem ipsum dolor sit. </button>
    <button @click="showB(true)"> 2.Lorem ipsum dolor sit. </button>
    <button @click="showC(true)"> 3.Lorem ipsum dolor sit. </button>
    <button @click="showD(true)"> 4.Lorem ipsum dolor sit. </button>
  </div>  
</div>
</template>

<script>
  export default {
    data() {
      return {
        chick: false,
        egg: false,
        Z: true,
        A: false,
        B: false,
        C: false,
        D: false
      }
    },
    methods: {
      showA(param) {
        this.Z = !param;
        this.A = param;
        return
      },
      showB(param) {
        this.A = !param;
        this.B = param;
        return
      },
      showC(param) {
        this.B = !param;
        this.C = param;
        return
      },
      showB(param) {
        this.c = !param;
        this.D = param;
        return
      },
    },
  }
</script>

<style scoped>
* {
  margin: 0;
  border: 0;
  box-sizing: border-box;
}

img {
  width: 50%;
}

.animation-box {
  width: 100vw;
  height: 100vh;
  border: black 5px solid;
}

.flex {
  display: flex;
}

.box1 {
  border: olivedrab 5px solid;
  display: inline-block;
  width: 100%;
  height: 100%;
}

.image-background {
  background-image: url("../assets/chicken-cute.svg");
  background-repeat: repeat-x;
  background-position: 33% 50%;
  background-size: contain;
  background-color: tomato;
}

.image-egg {
  border: 1px solid blue;
  justify-content: center;
}

.slight-shaking {
  animation: slight-shake 3s infinite;
  /* transform: translate3d(0, 0, 0); */
  /* backface-visibility: hidden; */
  perspective: 1000px;
}

@keyframes slight-shake {
  10%, 90% {
    transform: translate3d(-2px, 0, 0);
  }
  
  20%, 80% {
    transform: translate3d(2px, -1px, 0);
  }

  30%, 50%, 70% {
    transform: translate3d(-2px, 1px, 0);
  }

  40%, 60% {
    transform: translate3d(2px, 0, 0);
  }
}

.medium-shaking {
  animation: medium-shake 2s infinite;
  perspective: 1000px;
}

@keyframes medium-shake {
  10%, 90% {
    transform: translate3d(-4px, 5px, 0);
  }
  
  20%, 80% {
    transform: translate3d(4px, -5px, 0);
  }

  30%, 50%, 70% {
    transform: translate3d(-4px, 5px, 0);
  }

  40%, 60% {
    transform: translate3d(4px, -5px, 0);
  }
}

  .strong-shaking {
  animation: strong-shake 1s infinite;
  perspective: 1000px;
}

@keyframes strong-shake {
  10%, 90% {
    transform: translate3d(-5px, 5px, 0);
  }
  
  20%, 80% {
    transform: translate3d(5px, -5px, 0);
  }

  30%, 50%, 70% {
    transform: translate3d(-5px, 5px, 0);
  }

  40%, 60% {
    transform: translate3d(5px, -5px, 0);
  }
}

.stronger-shaking {
  animation: stronger-shake 1s infinite;
  perspective: 1000px;
}

@keyframes stronger-shake {
  10%, 90% {
    transform: translate3d(-10px, 10px, 0);
  }
  
  20%, 80% {
    transform: translate3d(10px, -10px, 0);
  }

  30%, 50%, 70% {
    transform: translate3d(-10px, 10px, 0);
  }

  40%, 60% {
    transform: translate3d(10px, -10px, 0);
  }
}

.opacity{
  opacity: 0.4;
}

.opacity--medium{
  opacity: 0.2;
}

.position-wrapper {
  position: relative;
}

.position {
  position: absolute;
}
</style>