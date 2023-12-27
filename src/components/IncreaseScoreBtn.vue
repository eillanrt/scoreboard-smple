<template lang="">
  <button @click="$emit('increaseBy', teamId, score)">+{{ score }}</button>
</template>
<script>
export default {
  name: 'IncrementBtn',
  props: {
    teamId: String,
    score: {
      type: Number,
      default: 0,
    },
  },
}
</script>
<style></style>
