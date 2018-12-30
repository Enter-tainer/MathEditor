<template>
<div>
  <h1>QAQ</h1>
  <textarea v-model="text"></textarea>
  <img :src="link">
</div>
</template>
<script lang="ts">
import Vue from 'vue'
export default Vue.extend({
  name: "index",
  mounted () {},
  data () {
    return {
      text: ''
    };
  },
  computed: {
    link () {
      return `https://www.zhihu.com/equation?tex=${encodeURI(this.text)}&preview=true`
    }
  },
  methods: {
    showClick () {
      this.showTip = true;
    }
  }
})
</script>
<style scoped>

</style>
