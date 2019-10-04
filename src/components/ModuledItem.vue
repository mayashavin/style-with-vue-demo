<template>
  <div :class="[item.container, mode]" :style="{ background: theme.defaultColor}">
    <img :src="src">
    <h3 :class="description.title">{{title}}</h3>
  </div>
</template>
<script>
export default {
  inject: ["viewMode", "theme"],
  props: {
    title: String,
    publicId: String,
    cloudName: String
  },
  computed: {
    src() {
      return `https://res.cloudinary.com/${this.cloudName}/image/upload/${
        this.publicId
      }.png`;
    },
    mode() {
      return this.viewMode.isGrid
        ? this.item.container_card
        : this.item.container_row;
    }
  }
};
</script>
<style module="item" lang="scss">
.container {
  border: 1px solid lightgray;
  padding: 5px;

  &:hover {
    background-color: #d3d3d363;
    cursor: pointer;
  }

  &_card {
    margin-right: 10px;
    margin-bottom: 10px;
    width: 220px;
    box-shadow: 0 1px 2px rgba(0, 0, 0, 0.2);
  }

  &_row {
    min-height: 60px;
    display: flex;
    width: 100%;

    img {
      height: 60px;
    }

    .title {
      border: none;
      font-size: 18px;
      margin-left: 10px;
      line-height: 2;
    }
  }
}
</style>
<style module="description">
.title {
  color: #842803;
  margin: 0;
  padding: 0.8rem 0;
  border-top: 1px solid lightgray;
}
</style>
