<template>
  <div class="container">
    <div class="markdownContainer">
      <h1 color="">文章</h1>
      <div v-html="markdownHtml"></div>
    </div>
  </div>
</template>

<script>
import ConsoleSource from 'raw-loader!../docs/console.md';

const marked = require('marked');

marked.setOptions({
  renderer: new marked.Renderer(),
  highlight: function(code, lang) {
    const hljs = require('highlight.js');
    const language = hljs.getLanguage(lang) ? lang : 'plaintext';
    return hljs.highlight(code, { language }).value;
  },
  // langPrefix: 'hljs language-', // highlight.js css expects a top-level 'hljs' class.
  pedantic: false,
  gfm: true,
  breaks: false,
  sanitize: false,
  smartLists: true,
  smartypants: false,
  xhtml: false
});


export default {
  data() {
    const result = marked.parse(ConsoleSource);
    return {
      markdownHtml: result,
    }
  },
}
</script>

<style lang="less" scoped>
.markdownContainer {
  height: 100%;
  padding: 30px;
  border-right: 1px dashed black;
}
.breakpoint {
  padding: 30px;
  height: 100%;
}

.markdownContainer {
  a{ color: #0645ad; text-decoration:none;}
  a:visited{ color: #0b0080; }
  a:hover{ color: #06e; }
  a:active{ color:#faa700; }
  a:focus{ outline: thin dotted; }
  a:hover, a:active{ outline: 0; }

  ::-moz-selection{background:rgba(255,255,0,0.3);color:#000}
  ::selection{background:rgba(255,255,0,0.3);color:#000}

  a::-moz-selection{background:rgba(255,255,0,0.3);color:#0645ad}
  a::selection{background:rgba(255,255,0,0.3);color:#0645ad}

  p{
  margin:1em 0;
  }

  img{
  max-width:100%;
  }

  h1,h2,h3,h4,h5,h6{
  font-weight:normal;
  color:#111;
  line-height:1em;
  }
  h4,h5,h6{ font-weight: bold; }
  h1{ font-size:2.5em; }
  h2{ font-size:2em; }
  h3{ font-size:1.5em; }
  h4{ font-size:1.2em; }
  h5{ font-size:1em; }
  h6{ font-size:0.9em; }

  blockquote{
    color:#666666;
    margin:0;
    padding-left: 3em;
    border-left: 0.5em #EEE solid;
  }
  hr { display: block; height: 2px; border: 0; border-top: 1px solid #aaa;border-bottom: 1px solid #eee; margin: 1em 0; padding: 0; }
  pre, code, kbd, samp { color: #000; font-family: monospace, monospace; _font-family: 'courier new', monospace; font-size: 0.98em; }
  pre { white-space: pre; white-space: pre-wrap; word-wrap: break-word; }

  b, strong { font-weight: bold; }

  dfn { font-style: italic; }

  ins { background: #ff9; color: #000; text-decoration: none; }

  mark { background: #ff0; color: #000; font-style: italic; font-weight: bold; }

  sub, sup { font-size: 75%; line-height: 0; position: relative; vertical-align: baseline; }
  sup { top: -0.5em; }
  sub { bottom: -0.25em; }

  ul, ol { margin: 1em 0; padding: 0 0 0 2em; }
  li p:last-child { margin:0 }
  dd { margin: 0 0 0 2em; }

  img { border: 0; -ms-interpolation-mode: bicubic; vertical-align: middle; }

  table {
  border-collapse: collapse;
  border-spacing: 0;
  width: 100%;
  }
  th { border-bottom: 1px solid black; }
  td { vertical-align: top; }
}
</style>
