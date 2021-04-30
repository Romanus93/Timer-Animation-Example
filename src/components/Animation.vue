<template>
  <div class="image-egg flex image-background" :class="{ 'sad-background-image': failure }">
    <img :class="shakingAnimation" :src="eggImage" v-show="success">
    <img class="translate-y" src="../assets/hatched-chick.svg" alt="" v-show="!success">
  </div>
</template>

<script>
  export default {
    props: {
      time: {
        type: Number
      },
    },
    data() {
      return {
        success: true,
        failure: false
      }
    },
    computed: {
      eggImage() {
        if(this.time > 20 || this.time === null) {
          return '/src/assets/white-egg.svg';
        } else if( this.time >= 1) {
          return '/src/assets/craked-egg.svg';
        } else if( this.time == 0 ) {
          setTimeout(()=> this.happy= false, 1000)
          return '/src/assets/born-egg.svg'
        } else {
          this.sad = true;
          return '/src/assets/broken-egg.svg'
        }
      },
      shakingAnimation() {
        if(this.time > 20 || this.time === null) {
          return {
            'slight-shaking': true 
          }
        } else if (this.time > 10) {
          return {
            'medium-shaking': true
          }
        } else if (this.time > 6) {
          return {
            'strong-shaking': true
          }
        } else if (this.time >= 1) {
          return {
            'stronger-shaking': true
          }
        } else if (this.time === 0) {
          return undefined;
        } else {
          return {
            'strong-shaking': true
          }
        }
      }
    }
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

.flex {
  display: flex;
}

.image-egg {
  border: olivedrab 5px solid;
  width: 100%;
  height: 100%;
  justify-content: center;
}

.image-background {
  background-image: url("../assets/chicken-cute.svg");
  background-repeat: repeat-x;
  background-position: 33% 50%;
  background-size: contain;
  background-color: #1565c0;
}

.sad-background-image {
  background-image: url("../assets/chicken-dark.svg");
}

.slight-shaking {
  animation: slight-shake 3s infinite;
  
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
  
}

@keyframes stronger-shake {
  10%, 90% {
    transform: translate3d(-10px, 12px, 0);
  }
  
  20%, 80% {
    transform: translate3d(10px, -11px, 0);
  }

  30%, 50%, 70% {
    transform: translate3d(-10px, 11px, 0);
  }

  40%, 60% {
    transform: translate3d(10px, -12px, 0);
  }
}

.translate-y {
    animation: translate-y 2s infinite linear;
  }

@keyframes translate-y {
  0%, 100% {
    transform: translate(0,0px);
  }
  25% {
    transform: translate(0,-5px);
  }
  50% { 
    transform: translate(0,5px);
  }
  75% {
    transform: translate(0,-5px);
  }
}  
</style>