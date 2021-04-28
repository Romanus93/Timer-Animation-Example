<template>
  <div>
    <div class="box1">
      <input type="number" placeholder="00" min="0" v-model.number="h" oninput="this.value = Math.floor(Math.abs(this.value))" />
      <input type="number" placeholder="00" max="60" v-model.number="m" oninput="this.value = (Math.floor(Math.abs(this.value))%60)" />
      <input type="number" placeholder="00" max="60" v-model.number="s" oninput="this.value = (Math.floor(Math.abs(this.value))%60)" />
    </div>
    <div class="box2">
      <h2>input</h2>
      <span>{{ _h }} : {{ _m }} : {{ _s }}</span> <span style="margin-left: 100px"> {{ totalTime }}</span>
    </div>
    <div class="box3">
      <button type="button" @click="setTimer"></button>
      <h2>output</h2>
      <span>{{ outPutH }} : {{ outPutM }} : {{ outPutS }}</span>
    </div>
    <div class="container">
      <Timer />
    </div>
  </div>
</template>

<script>
import Timer from '../components/Timer.vue'

  export default {
    components: { Timer },
    data() {
      return {
        ti: 1,
        h: '',
        m: '',
        s: '',
        outPutH: '00',
        outPutM: '00',
        outPutS: '00'
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
      totalTime() {
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
</style>