<template>
  <div style="color: red;">{{ counter }}</div>
  <Advanced :length="length" @callBack="callBack" />
</template>

<script>
import Advanced from "./components/advanced.vue";
export default {
  name: "App",
  components: { Advanced },
  data: () => ({
    length: 232312312213,
    counter: 1,
  }),
  methods: {
    callBack(param) {
      this.counter += +param;
    },
  },
  computed: {},
};
</script>

<style>
@import "./assets/theme.css";
[v-cloak] {
  display: none;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
