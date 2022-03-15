<template>
  <form ref="form" @submit.prevent="sendEmail">
    <!-- <label>Nome</label> -->
    <input type="text" name="user_name" placeholder="Nome"/>
    <!-- <label>Email</label> -->
    <input type="email" name="user_email" placeholder="Email"/>
    <!-- <label>Messaggio</label> -->
    <textarea name="message" rows="10" placeholder="Scrivi il tuo messaggio"></textarea>
    <input type="submit" value="Invia" class="form-btn"/>
  </form>
</template>

<script>
import emailjs from "@emailjs/browser";

export default {
  name: "ContactForm",
  methods: {
    sendEmail() {
      emailjs
        .sendForm(
          "service_sazce6r",
          "base_template",
          this.$refs.form,
          "TOZDo16km20APUhv6"
        )
        .then(
          (result) => {
            console.log("SUCCESS!", result.text);
          },
          (error) => {
            console.log("FAILED...", error.text);
          }
        );
    },
  },
};
</script>

<style lang="scss" scoped>
* {

  font-family: "DM Mono", monospace;
  font-size: 1rem;
}
form {
  display: flex;
  flex-direction: column;
  input, textarea {
    border: none;
    padding: .8rem;
    margin: .5rem 0 1rem;
  }
}
.form-btn { // Pulsante per tornare in cima e link
  text-decoration: underline;
  background: #ffafcc;
  padding: 1.2rem;
  color: #000;
  transition: all 0.2s ease;
  &:hover {
    background: #fff;
    cursor: pointer;
  }
      
}
</style>
