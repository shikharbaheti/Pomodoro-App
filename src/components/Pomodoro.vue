<template>
  <v-card>
    <v-tabs v-model="timerType" grow>
      <v-tab v-for="tab in tabTitles" :key="tab">{{tab}}</v-tab>
      <v-tabs-items v-model="timerType">
        <v-tab-item>
          <v-card color="basil" class="pa-5 d-flex flex-column justify-center align-center" flat>
            <h1 class="time">{{display.minutes}}:{{display.seconds}}</h1>
            <div class="button-group">
              <v-btn x-large color="primary">
                <v-icon left>mdi-play-circle-outline</v-icon>Start
              </v-btn>
              <v-btn x-large color="error">
                <v-icon left>mdi-stop-circle-outline</v-icon>Stop
              </v-btn>
              <v-btn x-large>
                <v-icon left>mdi-restart</v-icon>Reset
              </v-btn>
            </div>
          </v-card>
        </v-tab-item>
      </v-tabs-items>
    </v-tabs>
  </v-card>
</template>

<script>
export default {
  data() {
    return {
      display: {
        minutes: "00",
        seconds: "00"
      },

      totalSeconds: 25 * 60,
      timerType: 0,
      tabTitles: ["Pomodoro", "Short Break", "Long Break"]
    };
  },
  methods: {
    start() {
      setInterval(() => {}, 1000);
    },
    stop() {},
    reset() {}
  }
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