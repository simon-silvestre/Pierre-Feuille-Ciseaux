
<template>
    <div class="armeBorder" :style='{ background: couleur, boxShadow: shadow }' v-on="$parent.choix ? { click: () => choixArme() } : {}">
        <div class="armeBackground">
            <img :src="img" alt="">
        </div>
    </div>
</template>

<script>
export default {
    name: 'Arme',
    props: {
        couleur: String,
        img: String,
        arme: String,
        shadow: String
    },
    methods: {
        choixArme() {
            this.$parent.choix = false
            if(this.arme == 'paper') {
                this.$parent.index = 0
            }
            else if(this.arme == 'scissors') {
                this.$parent.index = 1
            }
            else {
                this.$parent.index = 2
            }
            this.$parent.ordinateur = Math.floor(Math.random() * 3)

            if(this.$parent.index != this.$parent.ordinateur) {
                if(this.$parent.index == 0 && this.$parent.ordinateur == 2 || this.$parent.index == 2 && this.$parent.ordinateur == 1 || this.$parent.index == 1 && this.$parent.ordinateur == 0 ) {
                    this.$parent.result = 'win'
                    this.$parent.score += 1
                }
                else {
                    this.$parent.result = 'lose'
                }
            }
            else {
                this.$parent.result = 'equal'
            }
        }
    }
}
</script>

<style lang="scss" scoped>
    .armeBorder {
        width: 200px;
        height: 200px;
    }
    .armeBackground {
        width: 156px;
        height: 156px;
        background: #fff;
        box-shadow: rgba(50, 50, 93, 0.25) 0px 21px 2px -12px inset;
    }
    img {
        width: 65px;
        height: 75px;
    }
    .armeBackground, .armeBorder {
        display: flex;
        justify-content: center;
        align-items: center;
        border-radius: 50%;
    }
</style>