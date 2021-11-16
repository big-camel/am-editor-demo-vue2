<template>
  <div>
    <am-toolbar v-if="engine" :engine="engine" :items="items" />
    <div ref="container"></div>
  </div>
</template>

<script>
import Engine from "@aomao/engine";
import AmToolbar, { ToolbarPlugin, ToolbarComponent } from "am-editor-toolbar-vue2";
import Codeblock, { CodeBlockComponent } from 'am-editor-codeblock-vue2'
import Bold from '@aomao/plugin-bold'
export default {
  name: "HelloWorld",
  components: {
    AmToolbar,
  },
  data: function () {
    return {
      engine: null,
      items: [['collapse'],['bold']]
    };
  },
  props: {
    msg: String,
  },
  mounted() {
    const engine = new Engine(
      this.$refs.container,
      {
        cards:[
          ToolbarComponent,
          CodeBlockComponent
        ],
        plugins: [
          ToolbarPlugin,
          Codeblock,
          Bold
        ]
      },
    );
    console.log(engine)
    this.engine = engine;
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
