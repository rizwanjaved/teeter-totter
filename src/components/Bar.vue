<template>
  <div class="bar" :style="inlineStyleSwing">
    <block v-for="block in leftSideBlocks" :block="block" :key="block.id" />
    <block
      v-for="block in rightSideBlocks"
      :block="block"
      :side="true"
      :key="block.id"
    />
  </div>
</template>

<script>
import Block from "./Block";
import { mapState, mapMutations } from "vuex";
import { ADD_RIGHT_SIDE_BLOCK } from "../constants";

export default {
  components: {
    Block
  },
  computed: {
    ...mapState(["rightSideBlocks", "leftSideBlocks"]),
    swingBending() {
      return this.$store.getters.swingBending;
    },
    inlineStyleSwing() {
      return {
        transform: `rotate(${this.swingBending / 2}deg)`
      };
    }
  },
  methods: {
    ...mapMutations({
      addRightBlock: ADD_RIGHT_SIDE_BLOCK
    })
  },
  beforeMount() {
    this.addRightBlock();
  }
};
</script>

<style lang="scss" scoped>
.bar {
  width: 100%;
  height: 5px;
  background-color: red;
  position: relative;
  transform: rotate(0deg);
  transition: transform 0.4s ease-in-out;
}
</style>
