<template>
  <div class="checkbox__container">
    <input :name="name" type="checkbox" :checked="isChecked" @change="onChange">
    <div class="label">{{label}}</div>
  </div>
</template>
<script>
export default {
  props: {
    name: String,
    isChecked: Boolean,
    label: String
  },
  methods: {
    onChange() {
      console.log("#####");
      this.$emit("change");
    }
  }
};
</script>
<style lang="scss" scoped>
.checkbox__container {
  display: flex;
  align-items: center;
  justify-content: center;
  margin: 10px;

  .label {
    margin-left: 5px;
  }
}
</style>
