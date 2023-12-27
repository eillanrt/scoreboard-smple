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
<style scoped>
.score {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100px;
  width: 100px;
  border: 1px solid black;
  border-radius: 10px;
  margin: 10px;
  font-size: 2rem;
  font-weight: bold;
  background-color: #f5f5f5;
  color: #000;
  transition: all 0.2s ease-in-out;
}
</style>
