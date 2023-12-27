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
  border-radius: 10px;
  margin: 50px 10px 10px;
}

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
