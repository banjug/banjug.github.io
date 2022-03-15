<template>
  <section>
    <div class="p-background">
      <div class="container">
        <div class="img">
          <span class="hello-text">{{ helloText }}</span> <!-- Animazione testo in loop sovraimposto all'immagine -->
          <img
            src="@/assets/portrait-min.webp"
            alt="Samuele Miotto portrait"
            class="portrait"
          />
        </div>
        <p>
          Benvenutǝ al mio portfolio. Mi chiamo Samuele e sono un web developer.
        </p>
        <p class="p-r">
          Troverai una selezione dei miei <a href="#works">migliori lavori</a>,
          qualche <a href="#about">informazione su di me</a>, e tutti
          <a href="#contacts">i miei contatti</a>, scorri in basso oppure clicca
          sulla sezione che ti interessa.
        </p>
      </div>
    </div>
  </section>
</template>
<script>
export default {
  name: "Presentation",
  data() {
    return {
      helloStrings: [".", "..", "...", "...Hello!"], // Lista delle stringhe da loopare
      loop: 0, // Valore del loop (aumenta al cambio di stringa)
      helloText: "", // Stringa attuale
    };
  },
  methods: {
    changeHello() {
      this.helloText = this.helloStrings[this.loop]; // Associa alla variabile helloText la stringa all'indice indicato dalla variabile loop
      this.loop = this.loop === this.helloStrings.length - 1 ? 0 : this.loop + 1; // Aumenta il valore di loop ogni volta che cambia stringa, se è arrivato alla fine della lista torna a 0
      return this.helloText;
    },
  },
  mounted() {
    setInterval(this.changeHello, 600); // Cambia stringa ogni 600 millisecondi
  },
};
</script>
<style lang="scss" scoped>
.p-background {
  display: flex;
  justify-content: center;
  .container {
    width: 70%;
    display: flex;
    flex-direction: column;
    @media (max-width: 960px) {
      width: 90%;
    }
    .img {
      position: relative;
      padding-top: 3rem;
      .hello-text {
        font-size: 2rem;
        position: absolute;
        @media (max-width: 960px) {
          left: 60%;
          font-size: 1.5rem;
        }
        left: 35%;
        bottom: 20%;
      }
      .portrait {
        @media (max-width: 960px) {
          width: 100%;
        }
        width: 50%;
        border-bottom: .7rem solid #ffafcc;
      }
    }
    p {
      width: 60%;
      font-size: 2rem;
      padding: 4rem 0;
      @media (max-width: 960px) {
        width: 100%;
        font-size: 1.5rem;
      }
      a {
        // Animazione dello sfondo con gradiente, il gradiente è grande il 400% del testo e all'hover viene spostato da una parte all'altra in un'animazione che dura 12 secondi
        background: linear-gradient(45deg, #f42, #a28, #42e, #a2f);
        background-clip: text;
        color: transparent;
        background-size: 400% 400%;
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
        &:hover {
          animation: Gradient 12s ease infinite;
        }
      }
    }
    .p-r {
      text-align: right;
      align-self: flex-end;
    }
    .p-c {
      margin: 0 auto;
    }
  }
}
</style>
