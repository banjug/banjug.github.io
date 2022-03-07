<template>
  <div id="app">
    <a href="#app" class="top-btn">Torna su</a>
    <EmojiSmile />
    <Presentation />
    <div class="divider"></div>
    <Works id="works" />
    <div class="divider"></div>
    <About id="about" />
    <div class="divider"></div>
    <Contacts id="contacts" />
    <MyFooter />
  </div>
</template>

<script>
import EmojiSmile from "./components/EmojiSmile.vue";
import Presentation from "./components/Presentation.vue";
import Works from "./components/Works.vue";
import About from "./components/About.vue";
import Contacts from "./components/Contacts.vue";
import MyFooter from "./components/MyFooter.vue";

export default {
  name: "App",
  components: {
    EmojiSmile,
    Presentation,
    Works,
    About,
    Contacts,
    MyFooter,
  },
};
</script>

<style lang="scss">
@import url("https://fonts.googleapis.com/css2?family=Archivo+Black&family=DM+Mono:ital@0;1&display=swap");

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
  scroll-behavior: smooth;
}
#app {
  position: relative;
  // text-align: center;
  // color: #2c3e50;
  // margin-top: 60px;
}

.top-btn {
  position: fixed;
  right: 5%;
  bottom: 5%;
  font-family: "DM Mono", monospace;
  background: #ffafcc;
  padding: 20px;
  z-index: 1;
  color: #000;
  transition: all 0.2s ease;
  @media screen and (max-width: 768px) {
    right: 10%;
    bottom: 15%;
  }
  &:hover {
    background: #fff;
  }
}

.divider {
  height: 20px;
  background-color: #ffafcc;
}
</style>
