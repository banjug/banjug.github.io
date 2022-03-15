<template>
  <div id="app">
    <a href="#app" class="btn top-btn" v-if="scroll > 800">Torna su</a>
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
  data() {
    return {
      scroll: 0,
    }
  },
  created() {
    window.addEventListener('scroll', this.getScroll)
  },
  methods: {
    getScroll() {
      this.scroll = window.scrollY;
    }
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
  font-family: "DM Mono", monospace;
  color: #ffafcc;
}

.btn {
  position: fixed;
  right: 5%;
  font-family: "DM Mono", monospace;
  background: #ffafcc;
  padding: 1.2rem;
  z-index: 1;
  color: #000;
  transition: all 0.2s ease;
  &.top-btn {
    bottom: 5%;
    @media (max-width: 960px) {
      right: 10%;
      bottom: 15%;
    }
      &:hover {
        background: #fff;
        @media (min-width: 960px) {
          + .links-btn {
            visibility: visible;
            opacity: 1;
          }
        }
      }
  }
  &.links-btn {
    display: flex;
    flex-direction: column;
    bottom: 15%;
    visibility: hidden;
    opacity: 0;
    transition: all 0.2s ease;
    padding: 0;
    &:hover {
      visibility: visible;
      opacity: 1;
    }
    a {
      padding: 1.2rem;
      color: #111;
      &:hover {
        color: #000;
        background: #fff;

      }
    }
  }
}

.divider {
  height: 1.2rem;
  background: repeating-linear-gradient(
    90deg,	
    #ffafcc,
    #ffafcc 3rem,
    #111 3rem,
    #111 6.2rem
  );
  background-size: 200% 100%;
  animation: Background 60s linear infinite;
  @keyframes Background {
    from {
      background-position: right;
    }
    to {
      background-position: left;
    }
  }
}
</style>
