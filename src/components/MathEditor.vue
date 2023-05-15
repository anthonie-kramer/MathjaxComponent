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
          <editor-content :editor="editor" />
        </td>
        <td>
          <button class @click="toggleEditor"></button>
        </td>
        <td>
          <vue-mathjax :formula="editorContent" />
        </td>
      </tr>
    </tbody>
  </table>
</template>

<script>
import { Editor, EditorContent } from '@tiptap/vue-3'
import StarterKit from '@tiptap/starter-kit'
import VueMathjax from 'vue-mathjax-next';
export default {
  components: {
    EditorContent,
    VueMathjax
  },
  name: "MathEditor",
  props: {
    msg: String,
  },
  data() {
    return {
      editor: null,
      showEditor: true
    };
  },
  computed: {
    editorContent() {
      if (this.editor) {
        let content = this.editor.getHTML();
        let strippedContent = '$$' + content.replace(/<\/?p>/g, '') + '$$';
        return strippedContent;
      }
      return '';
    }
  },
  methods: {
    toggleEditor() {
      this.showEditor = !this.showEditor;
    }
  },
  mounted() {
    this.editor = new Editor({
      content: 'x = {-b \\pm \\sqrt{b^2-4ac} \\over 2a}',
      extensions: [
        StarterKit,
      ],
    })
  },
  beforeUnmount() {
    this.editor.destroy()
  },
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
