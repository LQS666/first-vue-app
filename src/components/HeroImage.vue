<template>
    <div class="heroImage">

    </div>
</template>

<script>
export default {
  name: 'HeroImage',
};
</script>

<style lang="scss" scoped>
    .heroImage {
        position: fixed;
        top: 0;
        width: 100%;
        height: 100vh;
        z-index: -1;
        background-image: url('../assets/heroimage.jpg');
        background-repeat: no-repeat;
        background-size: cover;
        background-position: 80% 0%;
    }
</style>
