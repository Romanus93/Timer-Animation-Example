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
      <label for="hour"></label>
      <input id="hour" type="number" placeholder="00" min="0" v-model.number="h" oninput="this.value = Math.abs(this.value)" />
      <label for="minute"></label>
      <input id="minute" type="number" placeholder="00" min="0" v-model.number="m" oninput="this.value = Math.floor(this.value)" />
      <label for="second"></label>
      <input id="second" type="number" placeholder="00" min="0" v-model.number="s" oninput="this.value = Math.abs(this.value)" />
    </div>
    <div class="box2">
      <h2>input</h2>
      <span>{{ _h }} : {{ _m }} : {{ _s }}</span> <span style="margin-left: 100px"> {{ settingTime }}</span>
    </div>
    <div class="box3">
      <button type="button" @click="setTimer">Lorem ipsum dolor sit.</button>
      <h2>output</h2>
      <span>{{ outPutH }} : {{ outPutM }} : {{ outPutS }}</span>
    </div>
    <div class="container">
      <RefactoryTimer v-if="isVisual" :settingTime="settingTime" @checkTime="checkTime"/>
    </div>
    <!-- <div class="container">
      <Timer />
    </div> -->
    <div>
      <Animation :time="time" />
    </div>
  </div>
</template>

<script>
import Timer from '../components/Timer.vue'
import RefactoryTimer from '../components/RefactoryTimer.vue'
import Animation from '../components/Animation.vue'

  export default {
    components: {
      Timer,
      RefactoryTimer,
      Animation
    },
    data() {
      return {
        ti: 1,
        h: 0,
        m: 0,
        s: 0,
        outPutH: '00',
        outPutM: '00',
        outPutS: '00',
        propsBoolean: false,
        isVisual: false,
        time: null
      }
    },
    computed: {
      _h() {
        return Math.floor(this.h)
      },
      _m() {
        if(this.m >= 60) {
          this.m = 0;
          console.log('if -m');
          return this.m
        } else {
          console.log('else if - m');
          this.m = Math.floor(this.m);
          return Math.floor(this.m)
        }
      },
      _s() {
        if(this.s >= 60) {
          this.s = 0;
          console.log('if -s');
          return this.s
        } else {
          console.log('else if - s');
          this.s = Math.floor(this.s)
          console.log('else if - s');
          return Math.floor(this.s)
        }
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
      },
      fixM () {
        this.m = Math.floor(this.m % 60);
      },
      checkTime (param) {
        console.log('Container', param);
        this.time = param;
      }
    },
    created () {
      console.log('create');
      console.log(this.s);
    },
    mounted () {
      console.log('mount');
      console.log(this.s);
    },
    beforeUpdate () {
      console.log('beforeUpdate');
      console.log(this.s);
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
    100% {
      transform: rotate(360deg);
    }
  }

  .wrapper1 {
    width: 90vw;
  }

  .wrapper2 {
    background-color: tomato;
    height: 10px;
    width: 100%;
    transition-duration: 12s;
  }

  .animation {
    animation-timing-function: linear;
  }

  .rotateY {
    animation: rotationY 8s infinite linear;
    perspective: 1000px;
  }

  @keyframes rotationY {
    0% {
      transform: rotateY(0deg);
    }
    50% {
      transform: rotateY(360deg);
    }
    100% {
      transform: rotateY(0deg);
    }
  }
</style>