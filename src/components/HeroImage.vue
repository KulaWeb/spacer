<template>
    <div class="HeroImage"></div>
</template>

<script>
export default {
  name: 'HeroImage',
};
</script>

<style lang="scss" scoped>

    .HeroImage {
        background-image: url('../../assets/bg.jpg');
        background-position: 50% 0%;
        background-repeat: no-repeat;
        background-size: cover;
        position: fixed;
        width: 100%;
        height: 100vh;
        z-index: -1;
        top: 0;
    }
</style>
