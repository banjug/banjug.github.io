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
        <a class="email-btn">
          <font-awesome-icon icon="fa-solid fa-envelope" @click="emailClick"/>
          <span>Email</span>
        </a>
        
      </div>
      <transition name="expand">
        <ContactForm v-if="email"/>      
      </transition>
    </div>
  </section>
</template>

<script>
import ContactForm from './ContactForm.vue';

export default {
  components: { ContactForm },
  name: "Contacts",
  data() {
    return {
      email: false,
      links: [
        // Link dei contatti
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
      ],
    };
  },
  methods: {
    emailClick() {
      this.email = !this.email;
    }
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
    @media (max-width: 960px
    ) {
      width: 90%;
    }
    p {
      font-size: 2rem;
      width: 60%;
      @media (max-width: 960px
      ) {
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
        font-size: 4rem;
        margin-right: 2rem;
        transition: all 0.2s ease;
        display: flex;
        flex-direction: column;
        cursor: pointer;
        span {
          opacity: 0;
          font-size: 1rem;
          margin-top: 0.5rem;
          transition: all 0.2s ease;
          text-align: center;
          text-decoration: underline;
          @media (max-width: 960px
          ) {
            opacity: 1;
          }
        }
        @media (min-width: 960px
        ) {
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
  .expand-enter-active,
  .expand-leave-active {
    transition: max-height 1s ease;
    max-height: 100%;
  }

  .expand-enter,
  .expand-leave-to {
    max-height: 0;
    overflow: hidden;
  }
}
</style>
