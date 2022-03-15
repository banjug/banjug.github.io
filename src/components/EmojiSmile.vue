<template>
  <section>
    <div class="emoji-background">
      <!-- Animazione emoji in loop -->
      <h1 class="emoji">{{ emoji }}</h1>
      <h2 class="title">Hello, world.</h2>
    </div>
  </section>
</template>
<script>
export default {
  name: "EmojiSmile",
  data() {
    return {
      emojiList: ["~(｡0‿0｡)_", "_(｡-‿-｡)~", "~(｡-‿-｡)_", "_(｡0‿0｡)~"], // Lista delle emoji da loopare
      loop: 0, // Valore del loop (aumenta al cambio di emoji)
      emoji: "", // Emoji attuale
    };
  },
  methods: {
    changeSmile() {
      this.emoji = this.emojiList[this.loop]; // Associa alla variabile emoji l'emoji all'indice indicato dalla variabile loop (TODO si potrebbe randomizzare)
      this.loop = this.loop === this.emojiList.length - 1 ? 0 : this.loop + 1; // Aumenta il valore di loop ogni volta che cambia emoji, se è arrivato alla fine della lista torna a 0
      return this.emoji;
    },
  },
  mounted() {
    setInterval(this.changeSmile, 600); // Cambia emoji ogni 600 millisecondi
  },
};
</script>
<style lang="scss" scoped>
.emoji-background {
  margin: 0;
  height: 70vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;

  font-family: monospace;
  background-color: #f24;
  color: #eee;

  // Animazione dello sfondo con gradiente, il gradiente è grande il 400% del div e viene spostato da una parte all'altra in un'animazione che dura 12 secondi
  background: linear-gradient(45deg, #f42, #a28, #42e, #a2f); 
  background-size: 400% 400%;
  animation: Gradient 12s ease infinite;
    @keyframes Gradient {
      0% {
        background-position: 0% 50%;
      }
      50% {
        background-position: 100% 50%;
      }
      100% {
        background-position: 0% 50%;
      }
    }
  @media (max-width: 960px) {
    height: 50vh;
  }
  h1 {
    font-size: 8rem;
    font-family: "DM Mono", monospace;
    margin-bottom: 3rem;
    @media (max-width: 960px) {
        font-size: 40pt;
      }
  }
  h2 {
    font-size: 6rem;
  @media (max-width: 960px) {
      font-size: 2rem;
  }
  }
  
}
</style>
