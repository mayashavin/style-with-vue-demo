<template>
  <div id="app">
    <h1 class="title">The Pokemons</h1>
    <select default-value="currentThemeColor" @change="changeTheme">
      <option v-for="(key,value) in colors" :key="key" :value="key">{{value}}</option>
    </select>
    <Layout/>
  </div>
</template>

<script>
// import Layout from "./components/Layout";
import Layout from "./components/StyledLayout";

const colors = {
  default: "#fff",
  lightorange: "#fc9e2d",
  purple: "rgb(76, 76, 111)",
  darkpurple: "#111",
  pink: "pink"
};

export default {
  name: "App",
  components: {
    Layout
  },
  provide() {
    const theme = {};

    Object.defineProperty(theme, "defaultColor", {
      enumerable: true,
      get: () => this.currentThemeColor
    });

    return {
      theme: theme
    };
  },
  methods: {
    changeTheme(e) {
      console.log(e.target.value);
      this.currentThemeColor = e.target.value;
    }
  },
  data() {
    return {
      // colors: this.theme,
      colors: colors,
      currentThemeColor: colors.default
      // currentThemeColor: this.theme.default
    };
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

/* .app .title {
  color: #111;
} */
</style>
