<template>
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
<style scoped>
button {
  border: none;
  background: #f2f2f2;
  font-size: 18px;
  padding: 8px 16px;
  border-radius: 0.5rem;
  cursor: pointer;
}

button:hover {
  background: #e2e2e2;
}
</style>
