<template>
  <section>
    <div class="emoji-background">
      <h1 class="emoji">{{ emoji }}</h1>
      <h1 class="title">Hello, world.</h1>
    </div>
  </section>
</template>
<script>
export default {
  name: "EmojiSmile",
  data() {
    return {
      emojiList: ["~(｡0‿0｡)_", "_(｡-‿-｡)~", "~(｡-‿-｡)_", "_(｡0‿0｡)~"],
      loop: 0,
      emoji: "",
    };
  },
  methods: {
    changeSmile: function () {
      this.emoji = this.emojiList[this.loop];
      this.loop = this.loop === this.emojiList.length - 1 ? 0 : this.loop + 1;
      return this.emoji;
    },
  },
  mounted() {
    setInterval(this.changeSmile, 600);
  },
};
</script>
<style lang="scss" scoped>
.emoji-background {
  margin: 0;
  height: 70vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;

  font-family: monospace;
  background-color: #f24;
  color: #eee;

  background: linear-gradient(45deg, #f42, #a28, #42e, #a2f);
  background-size: 400% 400%;
  animation: Gradient 12s ease infinite;
  h1 {
    font-size: 50pt;
    font-family: "DM Mono", monospace;
  }
  .emoji {
    margin-bottom: 50px;
  }
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
}
</style>
