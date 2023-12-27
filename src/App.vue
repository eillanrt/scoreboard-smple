<template>
  <div class="score-app">
    <div class="scorers">
      <Scorer
        v-for="i in [1, 2]"
        :teamId="`team${i}`"
        :teamName="i === 1 ? team1.name : team2.name"
        @increaseBy="increaseBy"
        @decreaseBy="decreaseBy"
        :score="i === 1 ? team1.score : team2.score"
      />
    </div>
    <ResetScores @resetScores="resetScores" />
  </div>
</template>

<script>
import Scorer from './components/Scorer.vue'
import ResetScores from './components/ResetScores.vue'

export default {
  name: 'App',
  components: {
    Scorer,
    ResetScores,
    ResetScores,
  },
  data() {
    return {
      team1: {
        name: 'UNOR',
        score: 0 || Number(localStorage.getItem('team1Score')),
      },
      team2: {
        name: 'La salle',
        score: 0 || Number(localStorage.getItem('team2Score')),
      },
    }
  },
  methods: {
    increaseBy(teamId, points) {
      this[teamId].score += points
      localStorage.setItem(teamId + 'Score', this[teamId].score)
    },
    decreaseBy(teamId, points) {
      if (this[teamId].score - points < 0) {
        return
      }

      this[teamId].score -= points
      localStorage.setItem(teamId + 'Score', this[teamId].score)
    },
    resetScores() {
      this.team1.score = 0
      this.team2.score = 0
      localStorage.clear()
    },
  },
}
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
  font-family: 'Gantari', sans-serif;
}

body {
  background-color: #307790;
  color: white;
}

#app {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 100vh;
}

.score-app {
  width: 640px;
  display: flex;
  flex-direction: column;
}

.scorers {
  display: flex;
  justify-content: space-between;
}
</style>
