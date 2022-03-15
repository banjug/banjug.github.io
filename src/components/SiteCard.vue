<template>
  <div>
    <a :href="site.url" class="site-cont" target="_blank" v-if="!isMobile"> <!-- Sezione che appare se siamo su desktop -->
      <div @mouseenter="hoverCheck = 1" @mouseleave="hoverCheck = 0"> <!-- Controllo sull'hover -->
        <div class="overlay" v-show="hoverCheck === 1">
          <p>{{site.description}}</p>
        </div>
          <img :src="hoverCheck === 0 ? require(`../assets/${site.img}`) : require(`../assets/${site.gif}`)" :alt="site.title"> <!-- All'hover cambia l'immagine statica in una gif animata -->
      </div>
    </a>

    <a :href="site.url" class="site-cont" target="_blank" v-if="isMobile"> <!-- Sezione che appare se siamo su mobile -->
      <div class="overlay">
        <p>{{site.description}}</p>
      </div>
        <img :src="hoverCheck === 0 ? require(`../assets/${site.img}`) : require(`../assets/${site.gif}`)" :alt="site.title"> <!-- All'hover cambia l'immagine statica in una gif animata -->
    </a>

  </div>
</template>
<script>
export default {
    
  name: "SiteCard",
  props: {
      site: Object,
  },
  data() {
    return {
      hoverCheck: 0, // Booleano dell'hover
      isMobile: 0, // Booleano di controllo desktop o mobile
    }
  },
  created() {
  window.addEventListener('resize', this.onResize) // Controllo sulla dimensione del viewport chiamando onResize
  },
  methods: {
    onResize() {
    if (window.innerWidth > 960) { // Se il viewport è maggiore di 960px di larghezza siamo su desktop, altrimenti su mobile
      this.isMobile = 0
    } else {
      this.isMobile = 1
    }
  }
  },
    
}
</script>
<style lang="scss" scoped>
div {
  @media (min-width: 960px) {
    position: relative;
  }
    .site-cont {
    width: 100%;
    text-decoration: none;
    @media (max-width: 960px) {
      border-top: 1px solid #ffafcc;
      margin-top: 1rem;
    }
    img {
      width: 100%;
    max-height: 100%;
    object-fit: cover;
    }
    .overlay{
      display: flex;
      align-items: flex-end;
      transition: all .2s;
      // Su desktop l'overlay con la descrizione è posizionato direttamente al di sopra immagini e appare in hover, altrimenti viene spostato in alto e le lascia libere
      @media (min-width: 960px) { 
        position: absolute;
        top: 0;
        right: 0;
        bottom: 0;
        left: 0;
        background: rgb(17,17,17);
        background: linear-gradient(0deg, rgba(17,17,17,1) 0%, rgba(255,255,255,0) 50%);
      }
      p {
        color: #fff;
        padding: 1rem 1rem 2rem;
        @media (max-width: 960px) {
          padding: 1rem 0;
          border-top: 1px solid #ffafcc;
        }
      } 
    }
  }
}
</style>