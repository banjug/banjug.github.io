<template>
  <section>
    <div class="container">
      <div class="works-presentation">
        <h2>Cosa ho fatto{{ exclamation }}</h2> <!-- Animazione in loop dei punti alla fine del titolo -->
        <p>Qui c'è qualche esempio dei progetti portati a termine durante il bootcamp.</p>
        <p>Partendo layout grafici statici ho prodotto il front-end.</p>
        <p>Vuoi visitarli? Basta cliccare sull'immagine.</p>
      </div>
      <div class="grid-container">

        <!-- Componente per le card dei singoli siti -->
        <SiteCard
        v-for="site, i in sites"
        :key="i"
        :site="site"
         />


      </div>
    </div>
  </section>
</template>
<script>
import SiteCard from './SiteCard.vue';
export default {
  name: "Works",
  components: {
    SiteCard
  },
  data() {
    return {
      exclamationList: ['!', '??', '.', '!?', '..', '?', '!!', '?'], // Lista delle stringhe da loopare
      loop: 0, // Valore del loop (aumenta al cambio di stringa)
      exclamation: '', // Stringa attuale
      sites: [
        // Dati dei siti da passare al componente SiteCard
        {
          title: 'WhatsApp Web',
          url: 'https://clone-whatsapp-webapp.netlify.app/',
          img: 'site_whatsapp-min.png',
          gif: 'site_whatsapp.gif',
          description: "Riproduzione di Whatsapp Web in Vue.js. Ha una funzione di ricerca dei contatti, invio ed eliminazione dei messaggi, e controllo su data e ora di invio di questi ultimi.",
        },
        {
          title: 'Playstation',
          url: 'https://clone-playstation.netlify.app/',
          img: 'site_playstation-min.png',
          gif: 'site_playstation.gif',
          description: "Clone del sito di PlayStation. Ho utilizzato HTML e CSS senza un framework, c'è però qualche componente Bootstrap.",
        },
        {
          title: 'Spotify',
          url: 'https://clone-spotify-web.netlify.app/',
          img: 'site_spotify-min.png',
          gif: 'site_spotify.gif',
          description: "Qui ho riprodotto l'applicazione web di Spotify, anche questa è fatta senza l'utilizzo di un framework per il front-end. Nonostante questo il layuout è comunque completamente responsive. (Fino ad un certo punto)",
        },
        {
          title: 'MaxCoach',
          url: 'https://clone-maxcoach.netlify.app/',
          img: 'site_maxcoach-min.png',
          gif: 'site_maxcoach.gif',
          description: "Riproduzione di un tema WordPress, anche per questo sono partito da un'immagine statica per la riproduzione. È completamente progettato in Vue.js che mi ha reso semplicissimo il riutilizzo di determinati componenti.",
        },
      ]
    };
  },
  methods: {
      changeExclamaion() {
      this.exclamation = this.exclamationList[this.loop]; // Associa alla variabile exclamation la stringa all'indice indicato dalla variabile loop
      this.loop = this.loop === this.exclamationList.length - 1 ? 0 : this.loop + 1; // Aumenta il valore di loop ogni volta che cambia stringa, se è arrivato alla fine della lista torna a 0
      return this.exclamation;
    },
  },
  mounted() {
    setInterval(this.changeExclamaion, 300); // Cambia stringa ogni 300 millisecondi
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
    .works-presentation {
      margin-bottom: 2rem;
      > p {
        font-size: 1.2rem;
      }
      h2 {
        font-size: 4rem;
        margin-bottom: 3rem;
        @media (max-width: 960px) {
          font-size: 3rem;
        }
      }
    }
    .grid-container {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 2em 2em;
      grid-auto-flow: row;
      @media (max-width: 960px) {
        grid-template-columns: 1fr; 
      }
    }
  }

}
</style>
