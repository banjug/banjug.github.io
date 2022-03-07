<template>
  <section>
    <div class="container">
      <p>Ti piace quello che faccio?</p>
      <p>Contattami a questi link. A presto!</p>
      <div>
        <a v-for="(link, i) in links" :key="i" :href="link.url" target="_blank">
          <font-awesome-icon :icon="link.icon" />
          <span>{{ link.title }}</span>
        </a>
      </div>
    </div>
  </section>
</template>
<script>
export default {
  name: "Contacts",
  data() {
    return {
      links: [
        {
          title: "Github",
          url: "https://github.com/samuelemiotto",
          icon: "fa-brands fa-github",
        },
        {
          title: "LinkedIn",
          url: "https://www.linkedin.com/in/samuele-miotto/",
          icon: "fa-brands fa-linkedin",
        },
        {
          title: "Email",
          url: "mailto:mioto.samuele@gmail.com?subject=Conosciamoci",
          icon: "fa-solid fa-envelope",
        },
      ],
    };
  },
};
</script>
<style lang="scss" scoped>
section {
  background: #111;
  display: flex;
  justify-content: center;
  .container {
    width: 70%;
    display: flex;
    flex-direction: column;
    padding: 5rem 0;
    @media screen and (max-width: 768px) {
      width: 90%;
    }
    p {
      color: #ffafcc;
      font-family: "DM Mono", monospace;
      font-size: 2rem;
      width: 60%;
      @media screen and (max-width: 768px) {
        width: 100%;
        font-size: 1.5rem;
      }
    }
    div {
      display: flex;
      justify-content: center;
      padding: 5rem 0 0;
      a {
        color: #ffafcc;
        font-family: "DM Mono", monospace;
        font-size: 4rem;
        margin-right: 2rem;
        transition: all 0.2s ease;
        display: flex;
        flex-direction: column;
        span {
          opacity: 0;
          font-size: 1rem;
          margin-top: 0.5rem;
          transition: all 0.2s ease;
          text-align: center;
          @media screen and (max-width: 768px) {
            opacity: 1;
          }
        }
        @media screen and (min-width: 768px) {
          &:hover {
            color: #fff;
            span {
              opacity: 1;
            }
          }
        }
      }
    }
  }
}
</style>
