<template>
<div>
  <div class="animation-box">
    <div>
      <div class="box1 image-background">
        <div class="box-egg image-egg">
          <img class="slight-shaking" src="../assets/craked-egg.svg" alt="" width="100%" height="100%">
        </div>
      </div>
    </div>
  </div>
  <div class="animation-box">
    <div class="box1">
      <div class="image-craked-egg position-wrapper">
        <img class="medium-shaking position" src="../assets/white-egg.svg" alt="">
        <img class="medium-shaking opacity--medium position" src="../assets/craked-egg.svg" alt="">
      </div>
    </div>
  </div>
  <div class="animation-box">
    <div class="box1">
      <div class="image-craked-egg position-wrapper">
        <img class="strong-shaking position" src="../assets/craked-egg.svg" alt="">
        <img class="stronger-shaking opacity position" src="../assets/craked-egg-reverse.svg" alt="">
      </div>
    </div>
  </div>
  <div>
    <button @click="showChick(true)"> 성공 </button>
    <button @click="showEgg(true)"> 실패 </button>
  </div>  
</div>
</template>

<script>
  export default {
    data() {
      return {
        chick: false,
        egg: false
      }
    },
    methods: {
      showChick(param) {
        this.chick = param;
        return
      },
      showEgg(param) {
        this.egg = param
        return
      }
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
  width: 25%;
  height: 100%;
}

.animation-box {
  width: 100vw;
  height: 100vh;
  border: black 5px solid;
}

.box1 {
  border: olivedrab 5px solid;
  display: inline-block;
  width: 100%;
  height: 100%;
}

.box-egg {
  border: 5px tomato solid;
}

.image-background {
  background-image: url("../assets/chicken-cute.svg");
  background-repeat: repeat-x;
  background-position: 25% 50%;
  background-size: contain;
  background-color: tomato;
}

.image-egg {
  border: 1px solid blue;
  /* height: 50%;
  position: relative;
  left: 0%;
  top: 18%;
  z-index: 5; */
}

.image-craked-egg {
  width: 100%;
  height: 100%;
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
    transform: translate3d(-3px, 3px, 0);
  }
  
  20%, 80% {
    transform: translate3d(3px, -2px, 0);
  }

  30%, 50%, 70% {
    transform: translate3d(-3px, 2px, 0);
  }

  40%, 60% {
    transform: translate3d(3px, -3px, 0);
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
    transform: translate3d(-8px, 6px, 0);
  }
  
  20%, 80% {
    transform: translate3d(6px, -6px, 0);
  }

  30%, 50%, 70% {
    transform: translate3d(-6px, 6px, 0);
  }

  40%, 60% {
    transform: translate3d(6px, -8px, 0);
  }
}

.opacity{
  opacity: 0.02;
}

.opacity--medium{
  opacity: 0.2;
}

.position-wrapper {
  position: relative;
}

.position {
  position: absolute;
  right: 0
}

.flex {
  display: flex;
}
</style>