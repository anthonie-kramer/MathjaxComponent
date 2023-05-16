<template>
  <table class="matheditor">
    <thead>
      <tr>
        <th v-show="showEditor">LaTeX</th>
        <th></th>
        <th v-show="showEditor">Math Display</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td v-show="showEditor">
          <textarea v-model="formula"></textarea>
        </td>
        <td>
          <button class @click="toggleEditor"></button>
        </td>
        <td>
          <vue-mathjax :formula="formula" />
        </td>
      </tr>
    </tbody>
  </table>
</template>

<script>
import VueMathjax from 'vue-mathjax-next';
import { ref } from 'vue';

const formula = ref('');

export default {
  components: {
    VueMathjax
  },
  name: "MathEditor",
  props: {
    msg: String,
  },
  setup() {
  },
  data() {
    return {
      showEditor: true,
      formula
    };
  },
  methods: {
    toggleEditor() {
      this.showEditor = !this.showEditor;
    }
  }
};
</script>

<style scoped>
.matheditor {
  margin: 0 auto;
  padding: 10px;
  box-sizing: border-box;
}

.matheditor td {
  padding: 10px;
  width: auto;
  vertical-align: middle;
  text-align: left;
}

.matheditor th {
  color: #f15b6a;
}

button {
  height: 100px;
  border: 0;
}

button {
  height: 100px;
  border: 0;
}

button:hover {
  background-color: #f15b6a;
}
</style>
