<template>
  <div class="reset-wrap">
    <button @click="$emit('resetScores')">RESET</button>
  </div>
</template>
<script>
export default {
  name: 'ResetScores',
}
</script>
<style>
.reset-wrap {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 50px;
  border: 1px solid black;
  border-radius: 10px;
  margin: 10px;
}

.reset-wrap button {
  width: 30%;
  height: 100%;
  padding: 10px;
  border-radius: 10px;
  background-color: #f5f5f5;
  font-size: 1.5rem;
  font-weight: bold;
  cursor: pointer;
  transition: all 0.2s ease-in-out;
}
</style>
