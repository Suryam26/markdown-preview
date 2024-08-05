<script>
import {marked} from 'marked'
import {debounce} from 'lodash-es'

export default {
  data: () => ({
    input: '# Simple Markdown Preview',
    darkMode: false
  }),
  computed: {
    output() {
      return marked(this.input, {breaks: true})
    }
  },
  methods: {
    update: debounce(function (e) {
      this.input = e.target.value
    }, 100)
  }
}
</script>

<template>
  <div class="editor">
    <textarea class="input" :value="input" @input="update"></textarea>
    <div class="output" v-html="output"></div>
  </div>
</template>

<style>
body {
  margin: 0;
  font-family: "Open Sans", Arial, sans-serif;
}

.editor {
  height: 100vh;
  display: flex;
}

.input,
.output {
  overflow: auto;
  width: 50%;
  height: 100%;
  box-sizing: border-box;
  padding: 0 20px;
}

.input {
  border: none;
  border-right: 1px solid #ccc;
  resize: none;
  outline: none;
  background-color: #f6f6f6;
  font-size: 14px;
  font-family: 'Monaco', courier, monospace;
  padding: 20px;
}

a {
  text-decoration: none;
  color: #0066cc;
  transition: color 0.3s, text-decoration 0.3s;
}

a:hover {
  color: #004488;
  text-decoration: underline;
}

ul {
  list-style-type: disc;
  color: #444;
}

li {
  margin-bottom: 5px;
}

p {
  line-height: 1.45;
  padding: 0 10px;
}

code {
  font-family: "Courier New", monospace;
  background-color: #f2f2f2;
  padding: 2px 4px;
  border-radius: 3px;
  color: #333;
}

pre {
  font-family: "Courier New", monospace;
  background-color: #f2f2f2;
  padding: 10px;
  border-radius: 5px;
  overflow: auto;
  white-space: pre-wrap;
  color: #333;
  line-height: 1.45;
}

blockquote {
  border-left: 4px solid #999;
  margin: 0;
  padding: 10px 20px;
  background-color: #f7f7f7;
  color: #666;
  font-style: italic;
}

table {
  width: 100%;
  border-collapse: collapse;
  border: 1px solid #ddd;
}

th {
  background-color: #f2f2f2;
  border: 1px solid #ddd;
  padding: 8px;
  text-align: left;
}

td {
  border: 1px solid #ddd;
  padding: 8px;
}

hr {
  border: none;
  border-top: 1px solid #ddd;
  margin-bottom: 20px;
}

h1,
h2 {
  padding-bottom: 5px;
  border-bottom: 1px solid #ddd;
}
</style>
