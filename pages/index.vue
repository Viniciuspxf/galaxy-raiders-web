<template>
  <div id="canvas">
    <Game v-if="true" />
    <Menu v-if="true" />
  </div>
</template>

<script setup>
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
