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
        <div class="pause"  v-if="timer" @click="stopTimer">
          <i data-feather="square"></i>
        </div>
        <div class="stop" v-if="resetButton" @click="resetTimer">
          <i data-feather="rotate-cw"></i>
        </div>
        <div class="edit" v-if="!timer" @click="editTimer">
          <i data-feather="edit-2"></i>
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
    data() {
      return {
        timer: null,
        totalTime: (0.1 * 60),
        resetButton: false,
        title: "Countdown to rest time!",
        edit: false,
        isVisible: true
      }
    },
    methods: {
      startTimer: function() {
        this.timer = setInterval(() => this.countdown(), 1000); //1000ms = 1 second
        this.resetButton = true;
      },
      stopTimer: function() {
        clearInterval(this.timer);
        this.timer = null;
        this.resetButton = true;
      },
      // resetTimer: function() {
      //   this.totalTime = (25 * 60);
      //   clearInterval(this.timer);
      //   this.timer = null;
      //   this.resetButton = false;
      // },
      // editTimer: function() {
      //   this.edit = true;
      // },
      padTime: function(time){
        console.log(time);
        return (time < 10 ? '0' : '') + time;
      },
      countdown: function() {
        this.totalTime--;
      }
    },
    computed: {
      hours: function(){
        const hours = Math.floor(this.totalTime / (60*60))
        return this.padTime(hours);
      },
      minutes: function(){
        const minutes = Math.floor((this.totalTime - (this.hours * 60 * 60)) / 60);
        return this.padTime(minutes);
      },
      seconds: function() {
        const seconds = this.totalTime - (this.hours * 60 *60) - (this.minutes * 60);
        console.log(seconds);
        return this.padTime(seconds);
      },
      zeroTime: function() {
        console.log(this.totalTime);
        if(this.totalTime == 2) {
          clearInterval(this.timer)
          return true;
        } else {
          return false;
        }
      }
    },
    watch: {
      totalTime(newValue, oldValue) {
        if(newValue == 0){
          console.log('aaaa');
          // this.isVisible = false;
          clearInterval(this.timer)
          this.totalTime = 0;
        }
      },
    },
    mounted () {
      this.startTimer();
    },
    beforeUpdate() {
      console.log(this.totalTime );
      (this.totalTime != 0)||(clearInterval(this.timer))
      console.log(this.seconds);
      console.log(typeof this.seconds);
      console.log(this.zeroTime);
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