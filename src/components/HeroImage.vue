<template>
  <div class="hero-image-wrapper" />
</template>

<script>
export default {
  name: "HeroImage"
};
</script>

<style lang="scss" scoped>
.hero-image-wrapper {
  position: fixed;
  z-index: -1;
  width: 100%;
  height: 100vh;
  background: url("../assets/heroimage.jpg");
  background-repeat: no-repeat;
  background-position: center;
  background-size: cover;
}

.hero-image-wrapper::after {
  content: "";
  position: absolute;
  left: 0;
  right: 0;
  top: 0;
  bottom: 0;
  background-color: black;
  opacity: 0.55;
}
</style>
