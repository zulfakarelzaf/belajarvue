<template>
  <div>
    <v-app>
      <router-view></router-view>
      <v-snackbar
        v-model="snackbar.show"
        bottom
        right
        multi-line
        auto-height
        :timeout="5000"
        :color="snackbar.color"
      >
        {{snackbar.text}}
        <v-btn flat color="white" @click.native="snackbar.show = false">
          <v-icon>close</v-icon>
        </v-btn>
      </v-snackbar>
    </v-app>
  </div>
</template>

<script>
export default {
  data: () => ({
    snackbar: {
      show: false,
      text: "",
      color: ""
    }
  }),
  created() {
    window.getApp = this;
    window.getApp.$on("SHOW_SNACKBAR", snackbarData => {
      this.snackbar = snackbarData;
    });
  }
};
</script>
