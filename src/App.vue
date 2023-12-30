<template>
  <div class="score-app">
    <TeamNamesPopup @teamNamesSelected="closeModal" v-if="showModal" />
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
import TeamNamesPopup from './components/TeamNamesPopup.vue'

export default {
  name: 'App',
  components: {
    Scorer,
    ResetScores,
    TeamNamesPopup,
  },
  data() {
    return {
      team1: {
        name: localStorage.getItem('team1Name') || 'Team 1',
        score: Number(localStorage.getItem('team1Score')),
      },
      team2: {
        name: localStorage.getItem('team2Name') || 'Team 2',
        score: Number(localStorage.getItem('team2Score')),
      },
      showModal: localStorage.getItem('team1Name') === null,
    }
  },
  methods: {
    increaseBy(teamId, points) {
      this[teamId].score += points
    },
    decreaseBy(teamId, points) {
      if (this[teamId].score - points < 0) {
        return
      }

      this[teamId].score -= points
    },
    resetScores() {
      this.team1.score = 0
      this.team2.score = 0
      this.showModal = true
    },
    openModal() {
      this.showModal = true
    },
    closeModal(teamNames) {
      this.team1.name = teamNames.team1
      this.team2.name = teamNames.team2
      this.showModal = false
    },
  },
  watch: {
    'team1.score': function () {
      localStorage.setItem('team1Score', this.team1.score)
    },
    'team2.score': function () {
      localStorage.setItem('team2Score', this.team2.score)
    },
    'team1.name': function () {
      localStorage.setItem('team1Name', this.team1.name)
    },
    'team2.name': function () {
      localStorage.setItem('team2Name', this.team2.name)
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

@media (max-width: 640px) {
  .score-app {
    width: 100%;
  }
  .scorers {
    width: 90%;
    margin: 0 auto;
  }
}

@media (max-width: 480px) {
  #app {
    height: auto;
  }
  .scorers {
    flex-direction: column;
    align-items: center;
  }
}
</style>
