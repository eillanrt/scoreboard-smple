<template>
  <div class="modal">
    <div class="modal-content">
      <h2>Enter Team Names</h2>

      <form @submit.prevent="submitForm">
        <label for="team1">Team 1:</label>
        <input id="team1" v-model="team1Name" required />

        <label for="team2">Team 2:</label>
        <input id="team2" v-model="team2Name" required />

        <button type="submit">Submit</button>
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
      team1Name: '',
      team2Name: '',
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
}

.modal-content {
  background-color: #fefefe;
  margin: 15% auto;
  padding: 20px;
  border: 1px solid #888;
  width: 80%;
}

label {
  color: black;
}

.close {
  color: #aaa;
  float: right;
  font-size: 28px;
  font-weight: bold;
  cursor: pointer;
}

.close:hover,
.close:focus {
  color: black;
  text-decoration: none;
  cursor: pointer;
}
</style>
