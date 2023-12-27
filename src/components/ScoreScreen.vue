<template lang="">
  <div class="score">
    <h1>
      <slot></slot>
    </h1>
  </div>
</template>
<script>
export default {
  name: 'ScoreScreen',
  props: { score: Number, default: 0 },
}
</script>
<style scoped></style>
