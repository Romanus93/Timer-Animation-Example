<template>
  <div class="container">
    <div id="app">
      <div class="timer" v-if="isVisible">
        <span class="hour"> {{ hours }} </span>
        <span>:</span>
        <span class="minute">{{ minutes }}</span>
        <span>:</span>
        <span class="seconds">{{ seconds }}</span>
      </div>
      <div class="controls">
        <div class="start" v-if="!timer" @click="startTimer">
          <i data-feather="play" ></i>
        </div>
      </div>
      <div class="input">
        <input type="text" v-if="!zeroTime" >
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    props: {
      settingTime: {
        type: [ Number, String ],
        required: true 
      }
    },
    data() {
      return {
        timer: null,
        totalTime: this.settingTime,
        title: "Countdown to rest time!",
        isVisible: true
      }
    },
    methods: {
      startTimer: function() {
        this.timer = setInterval(() => this.totalTime--, 1000); //1000ms = 1 second
        this.resetButton = true;
      },
      twoDigitTime: function(time){
        console.log(time);
        return (time < 10 ? '0' : '') + time;
      }
    },
    computed: {
      hours: function(){
        const hours = Math.floor(this.totalTime / (60*60))
        return this.twoDigitTime(hours);
      },
      minutes: function(){
        const minutes = Math.floor((this.totalTime - (this.hours * 60 * 60)) / 60);
        return this.twoDigitTime(minutes);
      },
      seconds: function() {
        const seconds = this.totalTime - (this.hours * 60 *60) - (this.minutes * 60);
        return this.twoDigitTime(seconds);
      },
      // zeroTime: function() {
      //   console.log('computed',this.totalTime);
      //   if(this.totalTime == 2) {
      //     clearInterval(this.timer)
      //     return true;
      //   } else {
      //     return false;
      //   }
      // }
    },
    watch: {
      totalTime(newValue, oldValue) {
        if(newValue == 2){
          console.log('watch',this.totalTime);
          clearInterval(this.timer)
          this.totalTime = 0;
        }
      },
    },
    mounted () {
      this.startTimer();
    },
    beforeUpdate() {
      console.log('beforeUpdate',this.totalTime );
      // (this.totalTime == 3600) && this.startTimer();
      // (this.totalTime != 2)||(clearInterval(this.timer));
    }
  }
</script>

<style scoped>
html {
  font-size: 10px;
}

.container {
  height: 100vh;
  width: 100%;
  
  display: flex;
  align-items: center;
  justify-content: center;
  
  background-color: #222831;
}
  #app {
    display: flex; 
    flex-direction: column;
    align-items: center;
  }

  #app > * {
    margin-bottom: 2rem;
  }

  .timer {
    font-size: 9rem;
    color: #EEEEEE;
  }

  .controls > * {
      color: red;
      width: 100px;
      height: 100px;
      transition: 0.1s ease;
      background-color: orange;
      /* &:hover {
        cursor: pointer;
        transform: scale(1.2);
      } */
    }
  
  .controls .start {
      color: wheat;
      background-color: green;
  }

  .controls .pause {
      background-color: orange;
  }

  .controls .stop {
      background-color: blue;
  }

  .controls .edit {
      background-color: yellowgreen;
  }
  .input  input {
      background-color: #393E46;
      border: none;
      font-size: 2rem;
      padding: 1em;
      text-align: center;
      color: #EEEEEE;
    }
</style>