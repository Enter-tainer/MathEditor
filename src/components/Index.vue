<template>
  <div>
    <div class="mdui-row">
      <div class="mdui-col-xs-10 mdui-col-offset-xs-1 mdui-m-t-2">
        <pre>
            <codemirror v-model="text" :options="cmOptions"></codemirror>
        </pre>
      </div>
      <div class="mdui-card mdui-hoverable mdui-shadow-5 mdui-col-xs-10 mdui-col-offset-xs-1">
        <div class="mdui-card-content">
          <img :src="link" class="mdui-center mdui-m-t-1 mdui-m-b-1" :height="getScacle">
        </div>
        <div class="mdui-card-actions">
          <button
            class="mdui-btn mdui-ripple"
            @click="openDialog"
            mdui-dialog="{target: '#dialog'}"
          >Adjust scale</button>
        </div>
      </div>
    </div>
    <div class="mdui-dialog" id="dialog">
      <div class="mdui-dialog-title">调节缩放</div>
      <div class="mdui-dialog-content">
        滑动滑块以调节缩放（默认为 80px）
        <label class="mdui-slider mdui-slider-discrete mdui-m-t-2">
          <input v-model="scale" type="range" step="2" min="20" max="500">
        </label>
      </div>
      <div class="mdui-dialog-actions">
        <button class="mdui-btn mdui-ripple" mdui-dialog-close>ok</button>
      </div>
    </div>
  </div>
</template>
<script lang="ts">
import Vue from "vue";
import mdui from "mdui";
import "codemirror/mode/stex/stex.js";
import { codemirror } from "vue-codemirror";
export default Vue.extend({
  name: "index",
  components: { codemirror },
  data() {
    return {
      text: "\\sum_{i=1}^n\\frac{1}{i^2}=\\frac{\\pi^2}6",
      scale: 80,
      dialog: new mdui.Dialog("#dia", {}),
      cmOptions: {
        // codemirror options
        tabSize: 2,
        line: true
        // more codemirror options, 更多 codemirror 的高级配置...
      }
    };
  },
  methods: {
    openDialog() {
      mdui.updateSliders();
    }
  },
  computed: {
    link() {
      return `https://www.zhihu.com/equation?tex=${encodeURIComponent(
        this.text
      )}&preview=true`;
    },
    getScacle() {
      return `${this.scale}px`;
    }
  }
});
</script>
<style>
@import "codemirror/lib/codemirror.css";
@import "codemirror/theme/material.css";
@import "firacode/distr/fira_code.css";
.CodeMirror {
  height: auto;
}
.CodeMirror pre {
  font-family: "Fira Code Retina", Consolas, monospace;
  font-feature-settings: "liga";
}
</style>
