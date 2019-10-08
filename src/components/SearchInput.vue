<template>
  <div class="search-wrapper">
    <input
      :value="value"
      :class="{ dark }"
      type="text"
      class="search-input"
      placeholder="Input..."
      @input="handleChange"
    />
  </div>
</template>

<script>
export default {
  name: "SearchInput",
  props: {
    value: {
      type: String,
      required: true
    },
    dark: {
      type: Boolean,
      default: false
    }
  },
  methods: {
    handleChange(e) {
      this.$emit("input", e.target.value);
    }
  }
};
</script>

<style lang="scss" scoped>
.search-wrapper {
  display: flex;
  justify-content: center;
}

input[type="text"].search-input {
  border: 0;
  border-bottom: 2px solid white;
  text-align: center;
  font-size: 1.7em;
  font-weight: 700;
  background: transparent;
  padding-bottom: 0.3em;
  color: white;
  transition: box-shadow 0.5s;

  @media (min-width: 1024px) {
    font-size: 1.2em;
  }
}

input:focus {
  outline: none;
  box-shadow: 0 10px 20px -8px rgba(255, 255, 255, 0.2);
}

input[type="text"].dark {
  border-bottom-color: black;
  color: black;
}

input[type="text"].dark:focus {
  border-bottom-color: black;
  box-shadow: 0 10px 20px -8px rgba(0, 0, 0, 0.2);
}
</style>
