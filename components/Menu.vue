<template>
    <menu>
      <h1>Galaxy Raiders</h1>
      <nav>
        <button v-if="!onGame" @click="$emit('startGame')">Start Game</button>
        <button v-if="onGame" @click="$emit('continueGame')">Continue Game</button>
        <button @click="$emit('showLeaderboard')">Leader Board</button>
        <button @click="$emit('exitGame')">Exit</button>
      </nav>
    </menu>
</template>

<script>
export default {
  props: {
    onGame: Boolean
  },
  emits: ['startGame', 'continueGame' , 'showLeaderboard', 'exitGame'],
  mounted() {
    console.log("onGame:", this.onGame);
  }
}

</script>
  
<style scoped>
menu {
  position: absolute;

  height: inherit;
  width: inherit;

  background: url('~/assets/space.gif') center / cover no-repeat;
  
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

h1 {
  color: white;
  font-size: 4vw;
  text-transform: uppercase;

  z-index: 30;
}

nav {
  height: 50vh;
  width: 30vw;

  display: flex;
  flex-direction: column;
  justify-content: space-around;
  align-items: center;

  box-sizing: border-box;
  padding: 10vh 0.5vh;
}

nav button {
  height: 20%;
  width: 60%;

  font-size: 1.4vw;

  text-transform: uppercase;

  z-index: 30;
}
</style>
