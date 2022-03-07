<template>
  <section>
    <div class="p-background">
      <div class="container">
        <div class="img">
          <span class="hello-text">{{ helloText }}</span>
          <img
            src="@/assets/portrait.webp"
            alt="Samuele Miotto"
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
      helloText: "",
      helloStrings: [".", "..", "...", "...Hello!"],
      loop: 0,
    };
  },
  methods: {
    changeHello() {
      this.helloText = this.helloStrings[this.loop];
      this.loop =
        this.loop === this.helloStrings.length - 1 ? 0 : this.loop + 1;
      return this.helloText;
    },
  },
  mounted() {
    setInterval(this.changeHello, 600);
  },
};
</script>
<style lang="scss" scoped>
.p-background {
  background: #111;
  display: flex;
  justify-content: center;
  .container {
    width: 70%;
    display: flex;
    flex-direction: column;
    @media screen and (max-width: 768px) {
      width: 90%;
    }
    .img {
      position: relative;
      padding-top: 50px;
      .hello-text {
        color: #ffafcc;
        font-family: "DM Mono", monospace;
        font-size: 2rem;
        position: absolute;
        @media screen and (max-width: 768px) {
          left: 60%;
          font-size: 1.5rem;
        }
        left: 35%;
        bottom: 20%;
      }
      .portrait {
        @media screen and (max-width: 768px) {
          width: 100%;
        }
        width: 50%;
        border-bottom: 10px solid #ffafcc;
      }
    }
    p {
      width: 60%;
      color: #ffafcc;
      font-family: "DM Mono", monospace;
      font-size: 2rem;
      padding: 60px 0;
      @media screen and (max-width: 768px) {
        width: 100%;
        font-size: 1.5rem;
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
