<template>
  <div>
    <div class="p-background">
      <div class="container">
        <div class="img">
          <span class="hello-text">{{ helloText }}</span>
          <img src="@/assets/portrait.png" alt="Samuele Miotto" class="portrait">
        </div>
        <p
          v-for="(paragraph, i) in paragraphs"
          :key="i"
          :class="
            i + 1 != 0 && (i + 1) % 2 == 0
              ? 'p-r'
              : '' || (i + 1) % 3 == 0
              ? 'p-c'
              : ''
          "
        >
          {{ paragraph.text }}
        </p>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: "Presentation",
  data() {
    return {
      helloText: '',
      helloStrings: ['', '.', '..', '...', '...Hello!'],
      loop : 0,
      paragraphs: [
        {
          text: "Benvenutǝ al mio portfolio. Mi chiamo Samuele e sono un web developer.",
        },
        {
          text: "Troverai una selezione dei miei migliori lavori, qualche informazione su di me, e tutti i miei contatti, devi solo scrorrere in basso.",
        },
        {
          text: "Troverai una selezione dei miei migliori lavori, qualche informazione su di me, e tutti i miei contatti, devi solo scrorrere in basso.",
        },
      ],
    };
  },
  methods: {
    changeHello() {
      this.helloText = this.helloStrings[this.loop];
      this.loop = this.loop === this.helloStrings.length - 1 ? 0 : this.loop + 1;
      return this.helloText;
    }
  },
  mounted() {
    setInterval(this.changeHello, 600);
  }
};
</script>
<style lang="scss" scoped>
.p-background {
  background: #111;
  display: flex;
  justify-content: center;
  .container {
    position: re;
    width: 70%;
    display: flex;
    flex-direction: column;
    .img{
      position: relative;
      padding-top: 50px;
      .hello-text {
        color: #ffafcc;
        font-family: "DM Mono", monospace;
        text-align: left;
        font-size: 30pt;
        position: absolute;
        left: 35%;
        bottom: 20%;
      }
      .portrait {
        width: 50%;
        border-bottom: 10px solid #ffafcc;
      }
    }
    p {
      width: 60%;
      color: #ffafcc;
      font-family: "DM Mono", monospace;
      font-size: 30pt;
      padding: 60px 0;
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
