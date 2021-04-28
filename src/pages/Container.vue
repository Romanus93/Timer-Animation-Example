<template>
  <div>
    <div>
      <img class="rotate" width="100" height="100" src="../assets/sandclock.svg" alt="">
    </div>
    <!-- <div>아이콘 제작자 <a href="https://www.flaticon.com/kr/authors/smashicons" title="Smashicons">Smashicons</a> from <a href="https://www.flaticon.com/kr/" title="Flaticon">www.flaticon.com</a></div> -->
    <div>
      <img class="rotateY" width="100" height="100" src="../assets/weather-vane.svg" alt="">
    </div>
    <div class="wrapper1">
      <div class="wrapper2 animation"></div>
    </div>
    <div class="box1">
      <input type="number" placeholder="00" min="0" v-model.number="h" oninput="this.value = Math.floor(Math.abs(this.value))" />
      <input type="number" placeholder="00" max="60" v-model.number="m" oninput="this.value = (Math.floor(Math.abs(this.value))%60)" />
      <input type="number" placeholder="00" max="60" v-model.number="s" oninput="this.value = (Math.floor(Math.abs(this.value))%60)" />
    </div>
    <div class="box2">
      <h2>input</h2>
      <span>{{ _h }} : {{ _m }} : {{ _s }}</span> <span style="margin-left: 100px"> {{ settingTime }}</span>
    </div>
    <div class="box3">
      <button type="button" @click="setTimer"></button>
      <h2>output</h2>
      <span>{{ outPutH }} : {{ outPutM }} : {{ outPutS }}</span>
    </div>
    <div class="container">
      <RefactoryTimer v-if="isVisual" :settingTime="settingTime" />
    </div>
    <div class="container">
      <Timer />
    </div>
  </div>
</template>

<script>
import Timer from '../components/Timer.vue'
import RefactoryTimer from '../components/RefactoryTimer.vue'

  export default {
    components: { Timer, RefactoryTimer },
    data() {
      return {
        ti: 1,
        h: '',
        m: '',
        s: '',
        outPutH: '00',
        outPutM: '00',
        outPutS: '00',
        propsBoolean: false,
        isVisual: false
      }
    },
    computed: {
      _h() {
        return Math.floor(this.h)
      },
      _m() {
        (this.m > 60) && (this.m = Math.floor(this.s % 60))
        return Math.floor(this.m%60)
      },
      _s() {
        (this.s > 60) && (this.s = Math.floor(this.s % 60))
        return Math.floor(this.s%60)
      },
      settingTime() {
        let fullTime = this._h*3600 + this._m*60 + this._s;
        localStorage.setItem('time', fullTime);
        return fullTime; 
      }
    },
    methods: {
      setTimer() {
        let fullTime = localStorage.getItem('time');
        this.outPutH = Math.floor(fullTime/3600);
        this.outPutM = Math.floor((fullTime-this.outPutH*3600)/60);
        this.outPutS = fullTime-this.outPutH*3600-this.outPutM*60;
        this.isVisual = true;
      },
      trueBtn() {
        this.propsBoolean = true;
      }
    },  
  }
</script>

<style  scoped>
  .box1 {
    border: steelblue 5px solid;
  }
  .container {
    border: tomato 5px solid;
  }

  .rotate {
    animation: rotation 10s infinite steps(10, start);
  }

  @keyframes rotation {
    0% {
      transform: rotate(0deg);
    }
    /* 12.5% {
      transform: rotate(45deg);
    } */
    /* 25% {
      transform: rotate(90deg);
    } */
    /* 37.5% {
      transform: rotate(135deg);
    } */
    /* 50% {
      transform: rotate(180deg);
    } */
    /* 62.5% {
      transform: rotate(225deg);
    } */
    /* 75% {
      transform: rotate(270deg);
    } */
    /* 87.5% {
      transform: rotate(315deg);
    } */
    100% {
      transform: rotate(360deg);
    }
  }
/* <div class="wrapper1">
      <div class="wrapper2"></div>
    </div> */
  .wrapper1 {
    width: 90vw;
  }

  .wrapper2 {
    background-color: tomato;
    height: 10px;
    width: 100%;
    transition-duration: 12s;
    /* transition-timing-function: linear; */
    /* animation-timing-function: linear; */
  }

  .animation {
    animation-timing-function: linear;
    /* width: 100%; */
  }

  /* @keyframes slide {
    from {
      transform: scaleX(0);
    }
    to {
      transform: scaleX(100);
    }
  } */

  /*------*/
  .rotateY {
    animation: rotationY 8s infinite linear;
  }

  @keyframes rotationY {
    0% {
      transform: rotateY(0deg);
    }
    /* 12.5% {
      transform: rotate(45deg);
    } */
    /* 25% {
      transform: rotateY(90deg);
    } */
    /* 37.5% {
      transform: rotate(135deg);
    } */
    50% {
      transform: rotateY(360deg);
    }
    /* 62.5% {
      transform: rotate(225deg);
    } */
    /* 75% {
      transform: rotateY(270deg);
    } */
    /* 87.5% {
      transform: rotate(315deg);
    } */
    100% {
      transform: rotateY(0deg);
    }
  }
</style>