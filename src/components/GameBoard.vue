<template>
  <div class="playground">
    <Dropbox />
    <tetter-totter />
  </div>
</template>

<script>
import Dropbox from "./Dropbox";
import TetterTotter from "./TetterTotter";

export default {
  name: "GameBoard",
  components: {
    Dropbox,
    TetterTotter
  }
};
</script>

<style lang="scss" scoped>
.playground {
  width: 80%;
  height: 100%;
  margin: 0 auto;
  display: flex;
  flex-direction: column;
  padding-top: 1rem;
}
</style>
