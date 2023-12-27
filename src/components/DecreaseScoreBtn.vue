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
<style></style>
