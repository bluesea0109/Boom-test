<template>
  <div class="player">
    <div :class="['player-id', getPlayerClass()]">
      <span v-if="player.id >= 0">{{ player.id }}</span>
    </div>
    <div class="player-name">
      <span>{{ player.name }}</span>
    </div>
  </div>
</template>

<script>
export default {
  name: 'player',
  components: {},
  props: ['player', 'team'],
  methods: {
    getPlayerClass() {
      return Object.keys(this.team)
    },
  },
}
</script>

<style>
.player {
  display: flex;
}

.player-id {
  height: 50px;
  width: 50px;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: gray;
}

.player-name {
  height: 50px;
  width: 300px;
  display: flex;
  align-items: center;
  padding-left: 10px;
}

.player1 {
  border-top-left-radius: 10px;
}

.player2 {
  border-bottom-left-radius: 10px;
}
</style>
