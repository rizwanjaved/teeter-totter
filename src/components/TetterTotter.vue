<template>
  <div class="tetter-totter">
    <bar />
    <base-tringle />
  </div>
</template>

<script>
import Bar from "./Bar";
import BaseTringle from "./BaseTringle";

export default {
  components: {
    Bar,
    BaseTringle
  }
};
</script>

<style scoped>
.tetter-totter {
  height: 35%;
}
</style>
