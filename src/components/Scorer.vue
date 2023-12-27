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
