<template>
  <div class="wrapper">
    <h1 class="claim">SPACER</h1>
    <p class="subclaim">Begin your journay through our amazing galaxy</p>
    <p class="subclaim">Type anything space-related to start</p>
  </div>
</template>

<script>
export default {
  name: "Claim"
};
</script>

<style lang="scss" scoped>
.wrapper {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  text-align: center;
  padding: 2.6em;
  color: white;
}

.claim {
  font-size: 3.4em;
  font-weight: 800;
  margin: 0;

  @media (min-width: 768px) {
    font-size: 5.9em;
  }

  @media (min-width: 1024px) {
    font-size: 3.9em;
  }
}

.subclaim {
  font-size: 1em;
  margin-top: 1.2em 0 0 0;

  @media (min-width: 768px) and( max-width: 1023px) {
    font-size: 1.5em;
  }
}
</style>
