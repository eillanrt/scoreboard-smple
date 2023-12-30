<template>
  <div class="increase-score-btns-container">
    <IncreaseScoreBtn
      v-for="score in [1, 2, 3]"
      :key="score"
      @increaseBy="$emit('increaseBy', teamId, score)"
      :score="score"
      :teamId="teamId"
    />
  </div>
</template>
<script>
import IncreaseScoreBtn from './IncreaseScoreBtn.vue'

export default {
  name: 'IncrementBtns',
  components: {
    IncreaseScoreBtn,
  },
  props: {
    teamId: String,
  },
}
</script>
<style scoped>
.increase-score-btns-container {
  display: flex;
  justify-content: space-between;
  width: 100%;
  margin: 20px;
}
</style>
