<template>
<div>
  <div class="animation-box">
    <div class="image-background">
      <div class="box1" v-show="z">
        <div class="image-egg flex">
          <img class="slight-shaking" src="../assets/white-egg.svg" alt="">
        </div>  
      </div>
      <div class="box1" v-show="a">
        <div class="image-egg flex">
          <img class="medium-shaking" src="../assets/craked-egg.svg" alt="">
        </div>
      </div>
      <div class="box1" v-show="b">
        <div class="image-egg flex">
          <img class="strong-shaking" src="../assets/craked-egg.svg" alt="">
        </div>
      </div>
      <div class="box1" v-show="c">
        <div class="image-egg flex">
          <img class="strong-shaking" src="../assets/craked-egg.svg" alt="">
          <!-- <img class="stronger-shaking position opacity" src="../assets/craked-egg.svg" alt=""> -->
        </div>
      </div>
    </div>
    <div style="display:flex; justify-content: space-around">
      <button type="button" @click="showA(true)"> 1.Lorem ipsum dolor sit. </button>
      <button type="button" @click="showB(true)"> 2.Lorem ipsum dolor sit. </button>
      <button type="button" @click="showC(true)"> 3.Lorem ipsum dolor sit. </button>
    </div> 
  </div>
</div>
</template>

<script>
  export default {
    data() {
      return {
        chick: false,
        egg: false,
        z: true,
        a: false,
        b: false,
        c: false
      }
    },
    methods: {
      showA(param) {
        this.z = !param;
        this.a = param;
        return
      },
      showB(param) {
        console.log('b');
        this.a = !param;
        this.b = param;
        return
      },
      showC(param) {
        this.b = !param;
        this.c = param;
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
  width: 50%;
}

.animation-box {
  width: 100%;
  height: 100%;
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
</style>