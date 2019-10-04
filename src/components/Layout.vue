<template>
  <div class="layout__container">
    <check-box
      name="viewMode"
      :is-checked="isGrid"
      label="change to Grid"
      @change="onViewModeChange"
    />
    <h4>Current Theme: {{theme.defaultColor}}</h4>
    <div class="layout__grid_container">
      <moduled-item
        v-for="pokemon in pokemons"
        :key="pokemon.id"
        v-bind="pokemon"
        cloud-name="mayashavin"
      />
      <!-- <item v-for="pokemon in pokemons" :key="pokemon.id" v-bind="pokemon" cloud-name="mayashavin"/> -->
    </div>
  </div>
</template>
<script>
// import Item from "./Item";
import ModuledItem from "./ModuledItem";
import CheckBox from "./CheckBox";
import { database } from "../assets/data.json";

const pokemons = Object.keys(database.pokemons).map(id => ({
  ...database.pokemons[id],
  id: id
}));

export default {
  components: {
    // Item,
    CheckBox,
    ModuledItem
  },
  inject: ["theme"],
  provide() {
    const viewMode = {};

    Object.defineProperty(viewMode, "isGrid", {
      enumerable: true,
      get: () => this.isGrid
    });

    return {
      viewMode
    };
  },
  methods: {
    onViewModeChange() {
      this.isGrid = !this.isGrid;
    }
  },
  data() {
    return {
      isGrid: false,
      pokemons: pokemons
    };
  }
};
</script>
<style lang="scss" scoped>
.layout__grid_container {
  display: flex;
  flex-wrap: wrap;
  margin: 10px;
  justify-content: center;
  align-items: center;
}
</style>
