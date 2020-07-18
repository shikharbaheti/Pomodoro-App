<template>
  <v-card>
    <v-tabs @change="changeCurrentTimer" v-model="currentTimer" grow>
      <v-tab v-for="timer in timers" :key="timer.name">{{ timer.name }}</v-tab>
      <!-- <v-tabs-items v-model="currentTimer">
        <v-tab-item> </v-tab-item>
      </v-tabs-items> -->
    </v-tabs>
    <v-card class="pa-5 d-flex flex-column justify-center align-center" flat>
      <h1 class="time">{{ displayMinutes }}:{{ displaySeconds }}</h1>
      <div class="button-group">
        <v-btn @click="start" x-large color="primary">
          <v-icon left>mdi-play-circle-outline</v-icon>Start
        </v-btn>
        <v-btn @click="stop" x-large color="error">
          <v-icon left>mdi-stop-circle-outline</v-icon>Stop
        </v-btn>
        <v-btn
          @click="reset(timers[currentTimer].minutes)"
          :disabled="isRunning"
          x-large
        >
          <v-icon left>mdi-restart</v-icon>Reset
        </v-btn>
      </div>
    </v-card>
  </v-card>
</template>

<script>
export default {
  data() {
    return {
      isRunning: false,
      timerInstance: null,
      totalSeconds: 25 * 60,
      currentTimer: 0,
      timers: [
        { name: "Pomodoro", minutes: 25 },
        { name: "Short Break", minutes: 5 },
        { name: "Long Break", minutes: 10 },
      ],
    };
  },
  computed: {
    displayMinutes() {
      const minutes = Math.floor(this.totalSeconds / 60);
      return this.formatTime(minutes);
    },
    displaySeconds() {
      const seconds = this.totalSeconds % 60;
      return this.formatTime(seconds);
    },
  },
  methods: {
    formatTime(time) {
      if (time < 10) {
        return "0" + time;
      } else {
        return time.toString();
      }
    },
    start() {
      this.stop();
      this.isRunning = true;
      this.timerInstance = setInterval(() => {
        if (this.totalSeconds <= 0) {
          this.stop();
          return;
        }
        this.totalSeconds -= 1;
      }, 1000);
    },
    stop() {
      this.isRunning = false;
      clearInterval(this.timerInstance);
    },
    reset(minutes) {
      this.stop();
      this.totalSeconds = minutes * 60;
    },
    changeCurrentTimer(num) {
      console.log(num);
      this.currentTimer = num;
      this.reset(this.timers[num].minutes);
    },
  },
};
</script>

<style lang="sass" scoped>
// .v-card
//     width: 600px
.v-btn
    margin: 0 10px
.time
    font-size: 80px
    font-weight: 400
    text-align: center
</style>
