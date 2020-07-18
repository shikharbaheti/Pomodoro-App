<template>
  <v-app>
    <v-main>
      <v-container>
        <v-row>
          <v-col sm="6" offset-sm="3">
            <Pomodoro />
          </v-col>
        </v-row>
      </v-container>
      <v-container>
        <h5 class="text-h5 text-center">
          Developed by
          <a href="shikharbaheti.net" target="_blank"><b>Shikhar Baheti</b></a>
        </h5>
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
import Pomodoro from "./components/Pomodoro";

export default {
  name: "App",

  components: {
    Pomodoro,
  },

  data: () => ({
    //
  }),
};
</script>
