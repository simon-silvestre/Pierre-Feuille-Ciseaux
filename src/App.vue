<template>
  <div id="app">
    <Regles />
    <Score />
    <div class="armesContainer">
      <img class="triangle" src="@/assets/bg-triangle.svg" alt="triangle">
      <Arme class="papier" couleur="radial-gradient(hsl(230, 89%, 62%), hsl(230, 89%, 65%))" :arme="paper" />
      <Arme class="ciseaux" couleur="radial-gradient( hsl(39, 89%, 49%), hsl(40, 84%, 53%))" :arme="scissors" />
      <Arme class="pierre" couleur="radial-gradient(hsl(349, 71%, 52%), hsl(349, 70%, 56%))" :arme="rock" />
    </div>
    <button>rules</button>
  </div>
</template>

<script>
  import Score from './components/Score.vue'
  import Regles from './components/Règles.vue'
  import Arme from './components/Arme.vue'

export default {
  name: 'App',
  components: {
    Score,
    Regles,
    Arme
  },
  data() {
    return {
      paper: require('@/assets/icon-paper.svg'),
      scissors: require('@/assets/icon-scissors.svg'),
      rock: require('@/assets/icon-rock.svg')
    }
  }
}
</script>

<style lang="scss">
  @import url('https://fonts.googleapis.com/css2?family=Barlow+Semi+Condensed:wght@600;700&display=swap');
  * {
    box-sizing: border-box;
    padding: 0;
    margin: 0;
  }
  body {
    background: radial-gradient(hsl(214, 47%, 23%), hsl(237, 49%, 15%)) no-repeat;
  }
  #app {
    font-family: 'Barlow Semi Condensed', sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    width: 100%;
    height: 100vh;
  }
  .armesContainer {
    position: relative;
    margin: 100px auto;
    width: 480px;
    height: 430px;

    .triangle {
      position: absolute;
      top: 85px;
      left: 85px;
      z-index: -1;
    }
    .pierre, .papier, .ciseaux {
      position: absolute;
    }
    .papier {
      top: 0;
      left: 0;
    }
    .ciseaux {
      top: 0;
      right: 0;
    }
    .pierre {
      bottom: 0;
      left: calc(50% - 100px);
    }
  }
  button {
    position: absolute;
    bottom: 30px;
    right: 30px;
    width: 125px;
    height: 35px;
    border: 1px solid #fff;
    border-radius: 10px;
    background: transparent;
    color: #fff;
    text-transform: uppercase;
    font-weight: 600;
    letter-spacing: 1px;
    outline: none;
    cursor: pointer;
    transition: .1s ease;

    &:active {
      transform: scale(1.05);
    }
  }
</style>
