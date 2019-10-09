<template>
  <div :style="style" class="item" />
</template>

<script>
export default {
  name: "Item",
  props: {
    item: {
      type: Object,
      required: true
    }
  },
  data() {
    return {
      photo: this.item.links[0].href,
      title: this.item.data[0].title
    };
  },
  computed: {
    style() {
      return `background-image: url("${this.photo}")`;
    }
  }
};
</script>

<style lang="scss" scoped>
.item {
  width: 300px;
  height: 300px;
  background-position: 50%;
  background-size: cover;
  background-repeat: no-repeat;
}
</style>
