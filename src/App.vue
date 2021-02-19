<template>
  <div id="app">
    <transition name="fade">
      <Regles v-if="regles" />
    </transition>
    <Score />
    <transition name="fade">
      <div v-if="choix" class="armesContainer">
        <img class="triangle" src="@/assets/bg-triangle.svg" alt="triangle">
        <Arme :class="armes[0].nom" :couleur="armes[0].couleur" :img="armes[0].img" :arme="armes[0].nom" :shadow="armes[0].shadow" />
        <Arme :class="armes[1].nom" :couleur="armes[1].couleur" :img="armes[1].img" :arme="armes[1].nom" :shadow="armes[1].shadow" />
        <Arme :class="armes[2].nom" :couleur="armes[2].couleur" :img="armes[2].img" :arme="armes[2].nom" :shadow="armes[2].shadow" />
      </div>

      <div class="combat" v-if="!choix" >
        <div class="choixPersonnel">
          <p>you picked</p>
          <Arme class="combatArmes" :couleur="armes[index].couleur" :img="armes[index].img" :arme="armes[index].nom" :shadow="armes[index].shadow" />
        </div>
        <div class="combatResult">
          <p v-if="result == 'win'">you win</p>
          <p v-else-if="result == 'lose'">you lose</p>
          <p v-else-if="result == 'equal'">equality</p>
          <button @click="choix = true">play again</button>
        </div>
        <div class="choixOrdinateur">
          <p>the house picked</p>
          <Arme class="combatArmes" :couleur="armes[ordinateur].couleur" :img="armes[ordinateur].img" :arme="armes[ordinateur].nom" :shadow="armes[ordinateur].shadow" />
        </div>
      </div>
    </transition>
    <button class="reglesBouton" @click="regles = true">rules</button>
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
      armes: [
        {
          nom: 'paper',
          img: require('@/assets/icon-paper.svg'),
          couleur: "radial-gradient(hsl(230, 89%, 62%), hsl(230, 89%, 65%))",
          shadow: "0px 8px 0 0 #2a45c0"
        },
        {
          nom: 'scissors',
          img: require('@/assets/icon-scissors.svg'),
          couleur: "radial-gradient( hsl(39, 89%, 49%), hsl(40, 84%, 53%))",
          shadow: "0px 8px 0 0 #c76c1b"
        },
        {
          nom: 'rock',
          img: require('@/assets/icon-rock.svg'),
          couleur: "radial-gradient(hsl(349, 71%, 52%), hsl(349, 70%, 56%))",
          shadow: "0px 8px 0 0 #9f1834"
        }
      ],
      regles: false,
      choix: true,
      index: null,
      ordinateur: null,
      result: null,
      score: 0
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
  }
  .rock, .paper, .scissors {
    position: absolute;
    cursor: pointer;
    transition: .1s ease;

    &:active {
      box-shadow: none;
      transform: translateY(8px);
    }
  }
  .paper {
    top: 0;
    left: 0;
  }
  .scissors {
    top: 0;
    right: 0;
  }
  .rock {
    bottom: 0;
    left: calc(50% - 100px);
  }

  .reglesBouton {
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
  .fade-enter-active, .fade-leave-active {
      transition: opacity .5s
  }
  .fade-enter, .fade-leave-to {
      opacity: 0
  }

  .combat {
    display: flex;
    justify-content: space-between;
    max-width: 950px;
    height: 380px;
    margin: 100px auto;

    .choixPersonnel, .choixOrdinateur {
      display: flex;
      flex-direction: column;
      justify-content: space-between;
      align-items: center;
    }
    p {
      font-size: 25px;
      font-weight: 600;
      color: #fff;
      text-transform: uppercase;
      letter-spacing: 1px;
    }
    @media screen and (min-width: 970px) {
      .combatArmes {
        width: 280px;
        height: 280px;

        .armeBackground {
          width: 218px;
          height: 218px;

          img {
            width: 91px;
            height: 105px;
          }
        }
      }
    }
    .combatResult {
      margin: auto 0;
      text-align: center;
      p {
        font-size: 55px;
        font-weight: 800;
        text-transform: uppercase;
      }
      button {
        width: 220px;
        height: 50px;
        background: #fff;
        border-radius: 10px;
        color: hsl(229, 25%, 31%);
        border: none;
        outline: none;
        cursor: pointer;
        text-transform: uppercase;
        font-weight: 600;
        letter-spacing: 1px;
        margin-top: 20px;
      }
    }
  }
  @media screen and (max-width: 970px) {
    .combat {
      max-width: 700px;
      height: 300px;
    }
  }
  @media screen and (max-width: 750px) {
    .combat {
      max-width: 500px;
      height: 500px;
      flex-wrap: wrap;

      .choixPersonnel, .choixOrdinateur {
        flex-direction: column-reverse;
        height: 265px;
      }
      .combatResult {
        order: 3;
        width: 100%
      }
    }
  }
  @media screen and (max-width: 530px) {
    .armesContainer {
      max-width: 310px;
      height: 320px;
      margin: 7vh auto;
      padding: 0 10%;
    }
      .triangle {
        width: 200px!important;
        left: calc(50% - 100px)!important;
      }
      .armeBorder {
        width: 133px!important;
        height: 133px!important;

        .armeBackground {
          width: 104px;
          height: 104px;

          img {
            width: 43px;
            height: 50px;
          }
        }
      }
      .paper, .scissors {
        top: 25px;
      }
      .rock {
        left: calc(50% - 66.5px);
      }

  }
  .reglesBouton {
    right: calc(50% - 62.5px);
  }
  .combat {
    max-width: 310px;
    height: 55vh;
    margin: 10vh auto;

    .choixOrdinateur, .choixPersonnel {
      height: 200px;
    }
    p {
      font-size: 16px;
    }
  }
  @media screen and (max-width: 320px) {
    .combat {
      height: 63vh;
      margin: 4vh auto;
    }
  }
</style>
