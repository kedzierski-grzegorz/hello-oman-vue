<template>
  <div :class="[{ 'flex-start': step === 1 }, 'home-wrapper']">
    <transition name="move-down">
      <h1 v-if="step === 1" class="logo">SPACER</h1>
    </transition>
    <transition name="fade">
      <HeroImage v-if="step === 0" />
    </transition>
    <Claim v-if="step === 0" />
    <SearchInput v-model="searchValue" :dark="step === 1" @input="handleInput" />
    <div class="results">
      <div v-for="item in result">
        <p>{{ item.links[0].href }}</p>
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import Claim from "@/components/Claim.vue";
import SearchInput from "@/components/SearchInput.vue";
import HeroImage from "@/components/HeroImage.vue";

import debounce from "lodash.debounce";
import axios from "axios";

const API = "https://images-api.nasa.gov/search";

export default {
  name: "Home",
  components: {
    Claim,
    SearchInput,
    HeroImage
  },
  data() {
    return {
      searchValue: "",
      result: [],
      step: 0,
      loading: false
    };
  },
  methods: {
    handleInput: debounce(function() {
      this.loading = true;
      axios
        .get(`${API}?q=${this.searchValue}&media_type=image`)
        .then(response => {
          this.result = response.data.collection.items;
          this.loading = false;
          this.step = 1;
        })
        .catch(e => {
          console.log(e);
          this.loading = false;
        });
    }, 500)
  }
};
</script>

<style lang="scss" scoped>
.home-wrapper {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
  align-items: center;
  justify-content: center;
  position: relative;

  &.flex-start {
    justify-content: flex-start;
    padding-top: 15vh;
  }
}

.logo {
  position: absolute;
  top: 2vh;
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s;
}
.fade-enter,
.fade-leave-to {
  opacity: 0;
}

.move-down-enter-active,
.move-down-leave-active {
  transition: top 0.5s;
}
.move-down-enter,
.move-down-leave-to {
  top: -2em;
}
</style>
