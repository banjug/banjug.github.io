<template>
  <div id="app">
    <EmojiSmile />
    <Presentation />
    <div class="divider"></div>
  </div>
</template>

<script>
import EmojiSmile from "./components/EmojiSmile.vue";
import Presentation from "./components/Presentation.vue";

export default {
  name: "App",
  components: {
    EmojiSmile,
    Presentation,
  },
};
</script>

<style lang="scss">
@import url("https://fonts.googleapis.com/css2?family=Archivo+Black&family=DM+Mono:ital@0;1&display=swap");

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
#app {
  // text-align: center;
  // color: #2c3e50;
  // margin-top: 60px;
}

.divider {
  height: 20px;
  background-color: #ffafcc;
}
</style>
