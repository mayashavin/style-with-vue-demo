<template>
  <div class="item__container_card item__container">
    <img :src="src">
    <h3 class="title">{{title}}</h3>
  </div>
</template>
<script>
export default {
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
    }
  }
};
</script>
<style scoped lang="scss">
.item__container {
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

    .title {
      border: none;
      font-size: 18px;
      margin-left: 10px;
      line-height: 2;
    }
  }
}

.title {
  color: #842803;
  margin: 0;
  padding: 0.8rem 0;
  border-top: 1px solid lightgray;
}
</style>
