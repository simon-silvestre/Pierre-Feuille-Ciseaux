<template>
  <div class="scoreContainer">
    <img src="@/assets/logo.svg" alt="logo">
    <div class="scoreCard">
      <p>score</p>
      <p>{{ $parent.score }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Score',
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
  .scoreContainer {
    position: relative;
    max-width: 695px;
    height: 145px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    border: 2px solid hsl(217, 16%, 45%);
    border-radius: 15px;
    margin: 0 auto;
    top: 40px;
    padding: 15px 20px 15px 30px;
  }
  .scoreCard {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    width: 150px;
    height: 114px;
    background: #fff;
    border-radius: 8px;

    & p:nth-child(1) {
      position: relative;
      text-transform: uppercase;
      letter-spacing: 1px;
      color: hsl(229, 64%, 46%);
      top: 8px;
    }
    & p:nth-child(2) {
      font-size: 65px;
      font-weight: 700;
      color: hsl(229, 25%, 31%);
    }
  }

  @media screen and (max-width: 750px) {
    .scoreContainer {
      margin: 0 5%;
      height: 100px;
      border-radius: 8px;

      img {
        height: 100%;
      }
      .scoreCard {
        width: 100px;
        height: 76px;
        border-radius: 5px;

        & p:nth-child(1) {
          font-size: 14px;
        }
        & p:nth-child(2) {
          font-size: 43px;
        }
      }
    }
  }
  @media screen and (max-width: 530px) {
    .scoreContainer {
      top: 25px;
    }
  }
  @media screen and (max-width: 320px) {
    .scoreContainer {
      top: 10px
    }
  }
</style>