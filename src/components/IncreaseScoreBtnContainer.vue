<template lang="">
  <div>
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
<style lang=""></style>
