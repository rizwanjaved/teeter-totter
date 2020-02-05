<template>
  <v-app>
    <v-app-bar app class="text-xs-center">
      <strong>Insider’s Teeter Totter</strong>
    </v-app-bar>
    <v-content>
      <v-container fluid class="outer">
        <v-snackbar v-model="$store.state.alertStatus" :timeout="2000">
          Game is Over
          <v-btn color="blue" text @click="$store.state.alertStatus = false">
            Close
          </v-btn>
        </v-snackbar>
        <score-board></score-board>
        <game-board />
      </v-container>
    </v-content>
    <v-footer>
      <v-row justify="center" no-gutters>
        <v-btn
          v-if="isPaused"
          @click="togglePause"
          class="mx-2"
          fab
          dark
          small
          color="pink"
        >
          <v-icon dark>mdi-play</v-icon>
        </v-btn>
        <v-btn
          v-if="!isPaused"
          @click="resetGame"
          class="mx-2"
          fab
          dark
          small
          color="pink"
        >
          <v-icon dark>mdi-pause</v-icon>
        </v-btn>
        <v-btn @click="resetGame" class="mx-2" fab dark small color="pink">
          <v-icon dark>mdi-replay</v-icon>
        </v-btn>
      </v-row>
    </v-footer>
  </v-app>
</template>

<script>
import ScoreBoard from "@/components/ScoreBoard";
// import TetterTotter from "@/components/TetterTotter";
import GameBoard from "./components/GameBoard";
import { mapMutations, mapState } from "vuex";
import { TOGGLE_PAUSE } from "./constants";

export default {
  name: "App",
  components: {
    ScoreBoard,
    GameBoard
  },

  data: () => ({
    alert: true
    //
  }),
  computed: {
    ...mapState({
      isPaused: state => state.isPaused,
      alertStatus: state => state.alertStatus
    })
  },
  methods: {
    ...mapMutations({
      togglePause: TOGGLE_PAUSE
    }),
    resetGame() {
      this.$store.dispatch("START_NEW_GAME");
    }
  }
};
</script>

<style lang="scss">
.outer {
  height: 80vh;
  display: flex;
  flex-direction: column;
}
</style>
