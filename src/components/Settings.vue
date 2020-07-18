<template>
  <v-dialog v-model="dialog" persistent max-width="600px">
    <v-card> Placeholder </v-card>
  </v-dialog>
</template>

<script>
export default {
  props: {
    dialog: {
      type: Boolean,
      required: true,
    },
  },
};
</script>
