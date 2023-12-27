<template>
  <div>
    <div class="decrease-btn-wrap">
      <button @click="$emit('decreaseBy', teamId, 1)">DECREASE</button>
    </div>
  </div>
</template>
<script>
export default {
  name: 'DecreaseBtn',
  props: {
    teamId: String,
  },
}
</script>
<style scoped>
.decreaded-btn-wrap {
  display: flex;
  justify-content: space-between;
  width: 100%;
  margin: 20px;
}

button {
  border: none;
  background: #f2f2f2;
  font-size: 18px;
  padding: 8px 16px;
  border-radius: 0.5rem;
  cursor: pointer;
}
</style>
