<template>
  <div id="app">
    <a href="#app" class="btn top-btn">Torna su</a>
    <div class="btn links-btn">
      <a href="#works">Lavori</a>
      <a href="#about">Su di me</a>
      <a href="#contacts">Contatti</a>
    </div>
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

.btn {
  position: fixed;
  right: 5%;
  font-family: "DM Mono", monospace;
  background: #ffafcc;
  padding: 20px;
  z-index: 1;
  color: #000;
  transition: all 0.2s ease;
  &:hover {
    background: #fff;
    + .links-btn {
      visibility: visible;
      opacity: 1;
    }
  }
  &.top-btn {
    bottom: 5%;
    @media screen and (max-width: 768px) {
      right: 10%;
      bottom: 15%;
    }
  }
  &.links-btn {
    display: flex;
    flex-direction: column;
    bottom: 15%;
    visibility: hidden;
    opacity: 0;
    transition: all 0.2s ease;
    &:hover {
      visibility: visible;
      opacity: 1;
    }
    a {
      color: #000;
      &:nth-child(1),
      &:nth-child(2) {
        margin-bottom: 0.5rem;
      }
    }
  }
}

.divider {
  height: 20px;
  background-color: #ffafcc;
}
</style>
