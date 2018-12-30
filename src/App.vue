<template>
  <div>
    <div class="mdui-appbar mdui-appbar-fixed">
      <div class="mdui-toolbar mdui-color-theme">
        <a
          class="mdui-btn mdui-btn-icon"
        >
          <i class="mdui-icon material-icons">menu</i>
        </a>
        <a href="https://margatroid.xyz" class="mdui-typo-headline">Margatroid</a>
        <a href="/" class="mdui-typo-title">MathEditor</a>
      </div>
    </div>
    <div class="mdui-container mdui-typo">
      <router-view></router-view>
    </div>
  </div>
</template>

<script>
export default {
  name: "app"
};
</script>

<style>
@import 'mdui/dist/css/mdui.min.css';
</style>
