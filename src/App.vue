<template>
  <div id="app">
    <!-- Pulsante per tornare in cima (appare se lo scroll è superiore a 800px, scompare se inferiore) -->
    <a href="#app" class="btn top-btn" v-if="scroll > 800">Torna su</a>
    <!-- Pulsante con i link alle varie sezioni (appare all'hover sull'altro pulsante) -->
    <div class="btn links-btn">
      <a href="#works">Lavori</a>
      <a href="#about">Su di me</a>
      <a href="#contacts">Contatti</a>
    </div>

    <!-- Componenti VUE -->

    <!-- Componente con lo smile -->
    <EmojiSmile />
    <!-- Componente con foto, presentazione e link -->
    <Presentation />
    <!-- Divisore tratteggiato -->
    <div class="divider"></div> 
    <!-- Componente con lavori (portfolio) -->
    <Works id="works" />
    <!-- Divisore tratteggiato -->
    <div class="divider"></div> 
    <!-- Componente con descrizione dettagliata di chi sono -->
    <About id="about" />
    <!-- Divisore tratteggiato -->
    <div class="divider"></div> 
    <!-- Componente contatti personali -->
    <Contacts id="contacts" />
    <!-- Componente footer -->
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
      scroll: 0, // Valore dello scroll della pagina
    }
  },
  created() {
    window.addEventListener('scroll', this.getScroll) // Ascolta quanto la pagina è stata scrollata richiamando getScroll
  },
  methods: {
    getScroll() {
      this.scroll = window.scrollY; // Associa alla variabile scroll (data) il valore dello scroll verticale
    }
  },
};
</script>

<style lang="scss">
@import url("https://fonts.googleapis.com/css2?family=Archivo+Black&family=DM+Mono:ital@0;1&display=swap");

* { // Reset
  box-sizing: border-box;
  margin: 0;
  padding: 0;
  scroll-behavior: smooth;
}
#app {
  position: relative;
  font-family: "DM Mono", monospace;
  color: #ffafcc;
  background: #111;
}

.btn { // Pulsante per tornare in cima e link
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

.divider { // Divisore tratteggiato
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
