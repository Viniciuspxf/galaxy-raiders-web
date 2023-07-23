<template>
  <div id="canvas">
    <Game v-if="onGame" ref="gameRef" @pause-game="pauseGame"/>
    <Menu v-if="onMenu" @start-game="startGame" @continue-game="pauseGame" @exit-game="exitGame" :onGame="onGame"/>
  </div>
</template>

<script>
export default {
  data() {
    return {
      onGame: false,
      onMenu: true
    };
  },
  methods: {
    startGame() {
      this.onGame = true;
      this.onMenu = false;
    },
    pauseGame() {
      this.onMenu = !this.onMenu;
      this.$refs.gameRef.sendPauseCommand();
    },
    exitGame() {
      this.onGame = false;
    }
  }
}
</script>

<style>
#canvas {
  height: calc(100vh - 4rem);
  width: calc(100vw - 4rem);

  background-color: #36bbf5;

  padding: 2rem;
  overflow: hidden;

  position: relative;

  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
