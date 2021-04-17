<script>
export default {
  data() {
    return {
      email: "",
      password: "",
    };
  },
  methods: {
    async girisYap() {
      try {
        await this.$fire.auth.signInWithEmailAndPassword(
          this.email,
          this.password
        );
        this.$router.push("/");
      } catch (e) {
        alert(e);
      }
    },
  },
};
</script>

<template>
  <div class="container">
    <form @submit.prevent="girisYap">
      <div class="container">
        <h1>Giris Yap</h1>
        <hr />

        <label for="email"><b>Email</b></label>
        <input
          type="text"
          placeholder="tatarselcuk27@gmail.com"
          v-model="email"
          name="email"
          required
        />

        <label for="password"><b>Parola</b></label>
        <input
          type="password"
          placeholder="************"
          v-model="password"
          name="passsword"
          required
        />

        <button type="submit" class="registerbtn">Giris Yap</button>
      </div>
    </form>
  </div>
</template>

<style scoped>
body {
  font-family: Arial, Helvetica, sans-serif;
  background-color: black;
}

* {
  box-sizing: border-box;
}

.container {
  padding: 16px;
  background-color: white;
}

input[type="text"],
input[type="password"] {
  width: 100%;
  padding: 15px;
  margin: 5px 0 22px 0;
  display: inline-block;
  border: none;
  background: #f1f1f1;
}

input[type="text"]:focus,
input[type="password"]:focus {
  background-color: #ddd;
  outline: none;
}

hr {
  border: 1px solid #f1f1f1;
  margin-bottom: 25px;
}

.registerbtn {
  background-color: #4caf50;
  color: white;
  padding: 16px 20px;
  margin: 8px 0;
  border: none;
  cursor: pointer;
  width: 100%;
  opacity: 0.9;
}

.registerbtn:hover {
  opacity: 1;
}

a {
  color: dodgerblue;
}

.signin {
  background-color: #f1f1f1;
  text-align: center;
}
</style>