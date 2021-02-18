
<template>
    <div class="armeBorder" :style='{ background: couleur }'>
        <div class="armeBackground">
            <img :src="arme" alt="">
        </div>
    </div>
</template>

<script>
export default {
    name: 'Arme',
    props: {
        couleur: String,
        arme: String
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
    }
    img {
        width: 70px;
        height: 80px;
    }
    .armeBackground, .armeBorder {
        display: flex;
        justify-content: center;
        align-items: center;
        border-radius: 50%;
    }
</style>