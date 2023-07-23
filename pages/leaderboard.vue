<template>
    <section>
        <h2>Leaderboard</h2>
        <table>
            <tr v-for="round in leaderboard" :key="round.startTime">
                <td> {{ round.startTime }} </td>
                <td> {{ round.points }} </td> 
                <td> {{ round.numberOfDestroyedAsteroids }} </td>
            </tr>
        </table>
    </section>
</template>

<script>
export default {
  async setup() {
    const { data: leaderboard, pending: pending} = await $get("/space-field/leaderboard");
    return { leaderboard, pending }
  },
  beforeCreate() {
    this.leaderboard.forEach(element => {
        element.startTime = new Date(element.startTime).toString();
    });
  },
  methods: {
    async sendPauseCommand() {
      console.log("call command")
      await $post("/ship/commands", { command: "PAUSE_GAME" });
      this.isPaused = !this.isPaused;
    },
  }
}
</script>


<style scoped>
section {
  position: absolute;

  height: inherit;
  width: inherit;

  background: url('~/assets/space.gif') center / cover no-repeat;
  
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

h2 {
  color: white;
  font-size: 4vw;
  text-transform: uppercase;
}

td {
    color: white;
}
</style>