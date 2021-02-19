<template>
  <div class="scoreContainer">
    <img src="@/assets/logo.svg" alt="logo">
    <div class="scoreCard">
      <p>score</p>
      <p>{{ score }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Score',
  data() {
    return {
      score: 12,
    }
  }
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
    position: relative;
    width: 150px;
    height: 114px;
    background: #fff;
    border-radius: 8px;

    & p:nth-child(1) {
      position: absolute;
      text-transform: uppercase;
      letter-spacing: 1px;
      color: hsl(229, 64%, 46%);
      top: 15px;
      left: calc(50% - 23.5px);
    }
    & p:nth-child(2) {
      position: absolute;
      font-size: 65px;
      font-weight: 700;
      color: hsl(229, 25%, 31%);
      bottom: 11px;
      left: calc(50% - 26.5px);
    }
  }
</style>