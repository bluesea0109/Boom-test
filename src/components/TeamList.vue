<template>
  <div>
    <div class="add-team">
      <input type="text" v-model="player1" />
      <input type="text" v-model="player2" />
      <button @click="addTeam()">Add Team</button>
      <button @click="generateBrackets()">Generate Brackets</button>
    </div>
    <div class="bracket">
      <div v-for="(round, name) in rounds" :key="name">
        <draggable :class="'round'">
          <div v-for="(item, index) in round" :key="index">
            <div class="team-container">
              <div class="number">{{ index + 1 }}</div>
              <Team :team="item" />
            </div>
          </div>
        </draggable>
      </div>
    </div>
  </div>
</template>

<script>
import Team from './Team'
import draggable from 'vuedraggable'

export default {
  name: 'TeamList',
  props: {},
  data() {
    return {
      player1: '',
      player2: '',
      rounds: [],
      teamList: [],
    }
  },
  components: {
    Team,
    draggable,
  },
  methods: {
    addTeam() {
      if (!this.player1 || !this.player2) {
        return
      }
      this.teamList.push({
        player1: { id: 5, name: this.player1 },
        player2: { id: 6, name: this.player2 },
      })

      this.$set(this.rounds, 0, this.teamList)
    },

    generateBrackets() {
      let len = this.teamList.length / 2
      for (let i = 1; len >= 1; i++, len /= 2) {
        let temp = []
        for (let j = 0; j < len; j++) {
          temp.push({
            player1: { id: -1, name: '' },
            player2: { id: -1, name: '' },
          })
        }
        this.$set(this.rounds, i, temp)
      }
    },
  },
}
</script>

<style>
.bracket {
  display: flex;
}

.round {
  height: 100%;
  display: flex;
  flex-direction: column;
  justify-content: space-around;
  align-items: center;
  margin-left: 10px;
}

.team-container {
  display: flex;
  align-items: center;
}

.number {
  margin-right: 10px;
}
</style>
