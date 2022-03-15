<template>
  <section>
    <div class="container">
      <h2>
        Chi sono{{ exclamation }}
      </h2>
      <p>
        Mi chiamo Samuele.
      </p>
      <p>
        Pedalo e sviluppo siti, a volte contemporaneamente.
      </p>
      <p>
        Sono uno <span class="emphasize">sviluppatore web junior</span>, provengo da un <a href="https://boolean.careers/">coding bootcamp</a> di sei mesi ed ho un background nella <span class="emphasize">grafica</span> e nel <span class="emphasize">design</span>. 
      </p>
      <div class="grid-cont">
        <div class="grid-img">
          <img src="@/assets/portrait_2-min.jpg" alt="Samuele Miotto portrait">
          <span class="img-label">Questo sono io nella mia casa a Mestre.</span>
        </div>
        <div class="grid-p">
          <p class="r">
            Sono un ragazzo timido ma piaccio alle persone quando inizio ad aprirmi, o almeno così dicono le quattro persone cui l'ho fatto.<br> Ok ok, sono tre le persone.
          </p>
          <p class="r">
            Ho fatto qualche esperienza anche nel campo della ristorazione, quindi sono decisamente abituato a <span class="emphasize">lavorare in team</span> e ad affrontare e <span class="emphasize">risolvere i problemi</span> con velocità e precisione.
          </p>
          <p class="r">
            E allo stress. Si può dire che la ristorazione è stressante?
          </p>
          <p class="r">
            Sono da sempre un appassionato di informatica e tecnologia, passo il tempo su canali youtube e subreddit sull'argomento, ma solo nel tempo libero, non quando devo lavorare. Giuro.
          </p>
        </div>
      </div>
      <p>
        Durante il corso insieme ai miei compagni ho imparato le basi programmazione web, partendo da <span class="emphasize">HTML</span>, <span class="emphasize">CSS</span> e <span class="emphasize">JavaScript</span> arrivando a <span class="emphasize">Vue.js</span>. Chiamate API? No problem.
        Quando siamo passati al back-end siamo partiti studiando <span class="emphasize">mySQL</span> e <span class="emphasize">PHP</span>, passando dalle <span class="emphasize">query al server</span> alla <span class="emphasize">programmazione ad oggetti</span>, per poi completare il cerchio usando <span class="emphasize">Laravel</span>, con cui abbiamo messo insieme tutto quello che abbiamo imparato.
      </p>
      <p>
        E non mi sono mai divertito così tanto.
      </p>
      <p>
        Cerchiamo di continuare!
      </p>
    </div>
  </section>
</template>
<script>
export default {
  name: "About",
  data() {
      return {
        exclamationList: ['!', '??', '.', '!?', '..', '?', '!!', '?'],
        loop: 0,
        exclamation: ''
      };
    },
    methods: {
      changeExclamaion() {
      this.exclamation = this.exclamationList[this.loop];
      this.loop = this.loop === this.exclamationList.length - 1 ? 0 : this.loop + 1;
      return this.exclamation;
    },
  },
  mounted() {
    setInterval(this.changeExclamaion, 300);
  },
};
</script>
<style lang="scss" scoped>
section {
  display: flex;
  justify-content: center;
  .container {
    width: 70%;
    display: flex;
    flex-direction: column;
    padding: 5rem 0;
    @media (max-width: 960px) {
      width: 90%;
    }
    h2 {
      font-size: 4rem;
      @media (max-width: 960px) {
        font-size: 3rem;
      }
    }
    .grid-cont {
      @media (min-width: 960px) {
      display: grid; 
      grid-template-columns: 2fr 3fr; 
      gap: 0 0; 
      }
      .grid-img {
        position: relative;
        .img-label {
          position: absolute;
          top: 0;
          right: 0;
          padding: .5rem 1rem;
          font-size: .8rem;
          color: #fff;
          @media (max-width: 960px) {
            padding: 0;
            top: 2%;
          }
        }
        img {
          object-fit: cover;
          width: 100%;
          max-height: 100%;
          border-bottom: .7rem solid #ffafcc;
          @media (max-width: 960px) {
            margin: 2rem 0 1rem;
          }
        }
      }
      .grid-p {
        display: flex;
        flex-direction: column;
        justify-content: flex-end;
        padding-left: 1rem;
      }
    }
    p {
      width: 60%;
      margin: 1rem 0;
      font-size: 1.2rem;
      @media (max-width: 960px) {
        width: 100%;
      }
      &.r {
        width: 100%;
        text-align: right;
        align-self: stretch;
      }
      .emphasize, a {
        font-weight: bold;
        text-decoration: underline;
        color: #fff;
      }
      a {
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
  }
}
</style>
