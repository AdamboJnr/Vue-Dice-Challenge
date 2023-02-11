<script setup>
// import TheWelcome from '../components/TheWelcome.vue'
  import { ref, reactive, computed } from 'vue'

  const players = reactive({
    playerOne: 1,
    playerTwo: 1
  })

  const play = () => {
    players.playerOne = Math.floor(Math.random() * 6) + 1
    players.playerTwo = Math.floor(Math.random() * 6) + 1
  }

  const checkWinner = computed( () => {
    if(players.playerOne > players.playerTwo){
      return 'Player 1 Wins'
    }else if(players.playerTwo > players.playerOne){
      return 'Player 2 Wins'
    }else{
      return 'Draw'
    }
  })

</script>

<template>
  <div class="container">
    <h1>{{ checkWinner }}</h1>

    <div class="dice">
      <p>Player 1</p>
      <img :src="`./src/assets/dice${players.playerOne}.png`">
    </div>

    <div class="dice">
      <p>Player 2</p>
      <img :src="`./src/assets/dice${players.playerTwo}.png`">
    </div><br>

    <button @click="play">Play</button>
  </div>
</template>

<style scoped>
  .container {
  width: 70%;
  margin: auto;
  text-align: center;
}

.dice {
  text-align: center;
  display: inline-block;

}

body {
  background-color: #393E46;
}

h1 {
  margin: 30px;
  font-family: 'Lobster', cursive;
  text-shadow: 5px 0 #232931;
  font-size: 8rem;
  color: #4ECCA3;
}

p {
  font-size: 2rem;
  color: #4ECCA3;
  font-family: 'Indie Flower', cursive;
}

img {
  width: 80%;
}
</style>
