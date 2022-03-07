<template>
  <section>
    <div class="container">
      <p>Ti piace quello che faccio?</p>
      <p>Contattami a questi link. A presto!</p>
      <div>
        <a href="https://github.com/samuelemiotto">
          <font-awesome-icon icon="fa-brands fa-github" />
          <span>Github</span>
        </a>
        <a href="https://www.linkedin.com/in/samuele-miotto/">
          <font-awesome-icon icon="fa-brands fa-linkedin" />
          <span>LinkedIn</span>
        </a>
        <a href="mailto:mioto.samuele@gmail.com?subject=Conosciamoci">
          <font-awesome-icon icon="fa-solid fa-envelope" />
          <span>Email</span>
        </a>
      </div>
    </div>
  </section>
</template>
<script>
export default {
  name: "Contacts",
  data() {
    return {};
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
    p {
      color: #ffafcc;
      font-family: "DM Mono", monospace;
      font-size: 2rem;
      width: 60%;
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
        transition: all 0.2s ease-in-out;
        display: flex;
        flex-direction: column;
        span {
          opacity: 0;
          font-size: 1rem;
          margin-top: 0.5rem;
          transition: all 0.2s ease-in-out;
          text-align: center;
        }
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
</style>
