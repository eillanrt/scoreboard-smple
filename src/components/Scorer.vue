<template>
  <div class="score-wrap">
    <h1>{{ teamName }}</h1>
    <ScoreScreen> {{ score }} </ScoreScreen>
    <IncreaseScoreBtnContainer
      :teamId="teamId"
      @increaseBy="increaseBy"
      @decreaseBy="decreaseBy"
    />
    <DecreaseScoreBtn :teamId="teamId" @decreaseBy="decreaseBy" />
  </div>
</template>

<script>
import ScoreScreen from './ScoreScreen.vue'
import IncreaseScoreBtnContainer from './IncreaseScoreBtnContainer.vue'
import DecreaseScoreBtn from './DecreaseScoreBtn.vue'

export default {
  name: 'Scorer',
  components: {
    ScoreScreen,
    IncreaseScoreBtnContainer,
    DecreaseScoreBtn,
  },
  props: {
    teamName: String,
    teamId: String,
    score: Number,
  },
  methods: {
    increaseBy(teamId, score) {
      this.$emit('increaseBy', teamId, score)
    },
    decreaseBy(teamId, score) {
      this.$emit('decreaseBy', teamId, score)
    },
  },
}
</script>

<style scoped>
.score-wrap {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  width: 200px;
  border: 1px solid black;
  border-radius: 10px;
  margin: 10px;
  padding: 16px;
  background-color: #122329;
}

@media (max-width: 480px) {
  .score-wrap {
    width: 70%;
  }
}
</style>
