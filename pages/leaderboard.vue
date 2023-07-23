<template>
    <section>
        <h2>Leaderboard</h2>
        <table>
            <tr> 
              <th>Start Time</th>
              <th>Points</th>
              <th>Number Of Destroyed Asteroids</th>
            </tr>
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
    const { data: leaderboard } = await $get("/space-field/leaderboard");
    return { leaderboard }
  },
  beforeCreate() {
    this.leaderboard.forEach(element => {
        element.startTime = new Date(element.startTime).toString();
        element.points = Number.parseFloat(element.points).toFixed(2);
    });
  }
}
</script>


<style scoped>
* {
  color: white;
}

section {
  height: calc(100vh - 4rem);
  width: calc(100vw - 4rem);

  padding: 2rem;
  overflow: hidden;

  position: relative;

  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  align-items: center;
  
  background: url('~/assets/space.gif') center / cover no-repeat;
}

h2 {
  margin-top: 10vh;
  margin-bottom: 15vh;
  font-size: 4vw;
  text-transform: uppercase;
}

table {
  width: 60vw;
}

td, th {
  font-size: 1vw;
  text-align: center;
}

th {
  margin-bottom: 10px;
}

</style>