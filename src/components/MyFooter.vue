<template>
  <section>
    <p>Made with ❤️ and Vue.js</p>
    <p>Samuele Miotto / 2022</p>
  </section>
</template>
<script>
export default {
  name: "MyFooter",
  data() {
    return {};
  },
};
</script>
<style lang="scss" scoped>
section {
  padding: 2.5rem 0;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
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
  p {
    font-size: 0.8rem;
    &:first-child {
      margin-bottom: .7rem;
    }
  }
}
</style>
