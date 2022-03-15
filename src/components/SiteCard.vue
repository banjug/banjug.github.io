<template>
  <div>
    <a :href="site.url" class="site-cont" target="_blank" v-if="!isMobile">
      <div @mouseenter="hoverCheck = 1" @mouseleave="hoverCheck = 0">
        <div class="overlay" v-show="hoverCheck === 1">
          <p>{{site.description}}</p>
        </div>
          <img :src="hoverCheck === 0 ? require(`../assets/${site.img}`) : require(`../assets/${site.gif}`)" :alt="site.title">
      </div>
    </a>

    <a :href="site.url" class="site-cont" target="_blank" v-if="isMobile">
      <div class="overlay">
        <p>{{site.description}}</p>
      </div>
        <img :src="hoverCheck === 0 ? require(`../assets/${site.img}`) : require(`../assets/${site.gif}`)" :alt="site.title">
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
      hoverCheck: 0,
      isMobile: 0,
    }
  },
  created() {
  window.addEventListener('resize', this.onResize)
  },
  methods: {
    onResize() {
    if (window.innerWidth > 960) {
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