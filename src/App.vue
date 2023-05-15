<template>
  <MathEditor />
</template>

<script>
import MathEditorVue from "./components/MathEditor.vue";
export default {
  name: "App",
  components: {
    MathEditor: MathEditorVue,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
