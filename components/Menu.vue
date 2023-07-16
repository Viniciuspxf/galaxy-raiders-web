<template>
    <menu>
      <h1>Galaxy Raiders</h1>
      <nav>
        <button>Start Game</button>
        <button>Leader Board</button>
        <button>Exit</button>
      </nav>
    </menu>
</template>
  
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

  z-index: 10;
}

h1 {
  color: white;
  font-size: 4vw;
  text-transform: uppercase;
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
}
</style>
