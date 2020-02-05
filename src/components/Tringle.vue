<template>
  <div class="tringle" :style="tringleSize">{{ weight }}</div>
</template>

<script>
export default {
  data: () => ({}),
  props: {
    color: String,
    weight: Number
  },
  computed: {
    tringleWeight() {
      return this.weight * 10;
    },
    tringleSize() {
      return {
        "border-left": this.tringleWeight / 2 + "px solid transparent",
        "border-right": this.tringleWeight / 2 + "px solid transparent",
        "border-bottom": this.tringleWeight + "px solid " + this.color
      };
    }
  },
  methods: {}
};
</script>
<style lang="scss" scoped>
.tringle {
  width: 0;
  height: 0;
  // border-left: solid transparent;
  // border-right: solid transparent;
  // border-bottom: solid;
}
</style>
