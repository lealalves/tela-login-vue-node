<template>
  <div id="form-bg">
    <h1>Crie uma nova conta!</h1>
    <Input @custom-change="this.nome = $event" type="text" input="Nome" />
    <br />
    <Input @custom-change="this.email = $event" type="email" input="E-mail" />
    <br />
    <Input @custom-change="this.senha = $event" type="password" input="Senha" />
    <br />
    <Input
      @custom-change="this.confirmasenha = $event"
      type="password"
      input="Confirmar Senha"
    />
    <br />
    <Button @click="cadastrar" msg="Criar" />
    <p class="no-acc-txt">Já possui uma conta?</p>
    <router-link to="/"
      ><p class="new-acc-txt">Entrar com uma conta existente</p></router-link
    >
  </div>
</template>

<script>
import Input from "./form/Input.vue";
import Button from "./form/Button.vue";

export default {
  name: "FormRegister",
  components: {
    Input,
    Button,
  },
  data() {
    return {
      email: null,
      nome: null,
      senha: null,
      confirmasenha: null,
    };
  },
  methods: {
    async cadastrar() {
      const data = {
        email: this.email,
        nome: this.nome,
        senha: this.senha,
        confirmasenha: this.confirmasenha,
      };

      const dataJson = JSON.stringify(data);

      const req = await fetch(`${process.env.VUE_APP_API_URL}registrar`, {
        method: "POST",
        headers: { "Content-type": "application/json" },
        body: dataJson,
      });

      const res = await req.json();

      if (!res.ok) {
        console.log("Algo deu errado!");
        console.log(res.mensagem);
      } else {
        console.log(res.mensagem);
        console.log("Redirecionando para a página de login!");
        this.$router.push("/");
      }
    },
  },
};
</script>

<style scoped>
#form-bg {
  width: min(450px, 90vw);
  height: 500px;
  padding: 15px;
}
h1 {
  font-size: max(24px, 2.3vw);
}
</style>

