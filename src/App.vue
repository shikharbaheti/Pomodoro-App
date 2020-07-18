<template>
  <v-app>
    <v-main>
      <v-container fluid>
        <v-row>
          <v-col sm="6" offset-sm="3">
            <Pomodoro :dialog="dialog" :closeDialog="closeDialog" />
          </v-col>
          <v-btn
            @click="dialog = true"
            color="primary"
            dark
            medium
            top
            right
            fab
            ><v-icon>mdi-cog-outline</v-icon></v-btn
          >
        </v-row>
        <h5 class="text-h5 pa-5 mt-4 text-center">
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

  data() {
    return {
      dialog: false,
    };
  },

  methods: {
    closeDialog() {
      this.dialog = false;
    },
  },
};
</script>
