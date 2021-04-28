<template>
  <div>
    <h3>Hellow! </h3>
    <section class="flex timer-box">
      <div>
        {{displayDays}}
        <div>days</div>
      </div>
      <span>:</span>
      <div>
        {{displayHours}}
        <div>hours</div>
      </div>
      <span>:</span>
      <div>
        {{displayMinutes}}
        <div>minutes</div>
      </div>
      <span>:</span>
      <div>
        <div>{{displaySeconds}}</div>
        <div>seconds</div>
      </div>
    </section>
  </div>
</template>

<script>
  export default {
    data: () => ({
      displayDays: 0,
      displayHours: 0,
      displayMinutes: 0,
      displaySeconds: 0
    }),
    computed: {
      _seconds: () => 1000,
      _minutes() {
        return this._seconds * 60;
      },
      _hours() {
        return this._minutes * 60;
      },
      _days() {
        return this._hours * 24;
      }
    },
    created () {
      console.log('hi');
      
      let hour =(new Date()).setHours(4);
      console.log(hour);
    },
    mounted () {
      console.debug('hi timer');
      // this.showRemaining();
      // this.showHi();
      console.log('time out.')
    },
    beforeUpdate() {
      console.log('before Update');
    },
    methods: {
      showHi() {
        const timer = setInterval(() => {
          let count = 0;
          count += 1;
          console.log(count);
          if(count > 0) {
            clearInterval(timer);
            console.log('10넘음');
            return
          }
          console.log(count);
        }, 1000)
      }
      ,
      showRemaining() {
        const timer = setInterval(()=> {
          const now = new Date();
          console.debug(now);
          const end = new Date(2021, 0, 0, 22, 0, 0, 0 );
          console.debug(end);
          const distance = end.getTime() - now.getTime();
          // console.debug(distance);
          if (distance < 0) {
            clearInterval(timer);
            return;
          }

          const days = Math.floor(distance / this._days);
          console.debug(days);
          const hours = Math.floor((distance % this._days) / this._hours );
          console.debug(hours)
          const minutes = Math.floor((distance % this._hours) / this._minutes );
          console.debug(minutes)
          const seconds = Math.floor((distance % this._minutes) / this._seconds );
          this.displayMinutes = minutes < 10 ? "0" + minutes : minutes;
          console.log(this.displayMinutes);
          this.displaySeconds = seconds < 10 ? "0" + seconds : seconds;
          this.displayHours = hours < 10 ? "0" + hours : hours;
          this.displayDays = days < 10 ? "0" + days : days;
        }, 5000);
      },
      
    }
  } 
</script>

<style scoped>
  .flex {
    display: flex;
  }
  .timer-box {
    justify-content: center;
  }
  .timer-box > div {
    margin-left: 20px;
  }
</style>
