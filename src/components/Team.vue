<template>
  <div class="team">
    <Player :player="team.player1" :team="team" />
    <div class="line"></div>
    <Player :player="team.player2" :team="team" />
  </div>
</template>

<script>
import Player from './Player'

export default {
  name: 'team',
  components: { Player },
  props: ['team'],
}
</script>

<style>
.team {
  width: 350px;
  height: 100px;
  background-color: darkgray;
  border-radius: 10px;
  cursor: pointer;
  margin-top: 5px;
  margin-bottom: 5px;
}

.line {
  width: 350px;
  border-bottom: 0.1px solid black;
}
</style>
