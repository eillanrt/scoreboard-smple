<template>
  <div class="modal">
    <div class="modal-content">
      <h2>Enter Team Names</h2>

      <form @submit.prevent="submitForm">
        <div>
          <label for="team1">Team 1:</label><br />
          <input id="team1" v-model="team1Name" required />
        </div>
        <div>
          <label for="team2">Team 2:</label><br />
          <input id="team2" v-model="team2Name" required />
        </div>
        <div>
          <button type="submit">Submit</button>
        </div>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  name: 'TeamNamesPopup',
  props: {
    showModal: Boolean,
  },
  data() {
    return {
      team1Name: localStorage.getItem('team1Name') || '',
      team2Name: localStorage.getItem('team2Name') || '',
    }
  },
  methods: {
    openModal() {
      this.$emit('openModal')
    },
    closeModal() {
      this.$emit('closeModal')
    },
    submitForm() {
      this.$emit('teamNamesSelected', {
        team1: this.team1Name,
        team2: this.team2Name,
      })

      this.closeModal()
    },
  },
}
</script>

<style scoped>
.modal {
  position: fixed;
  z-index: 1;
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
  overflow: auto;
  background-color: rgba(0, 0, 0, 0.4);
  color: black;
}

.modal-content {
  background-color: #fefefe;
  margin: 15% auto;
  padding: 20px;
  border: 1px solid #888;
  width: 80%;
}

form > div {
  margin: 0 auto 15px;
  text-align: center;
}

label {
  display: block;
  margin-bottom: 5px;
  font-weight: bold;
  font-size: 24px;
}

input {
  width: 60%;
  padding: 16px 8px;
  box-sizing: border-box;
  font-size: 24px;
}

button {
  background-color: #4caf50;
  color: white;
  padding: 10px 15px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}
</style>
