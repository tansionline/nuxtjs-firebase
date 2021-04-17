<script>
export default {
  methods: {
    async writeToFirestore() {
      const messageRef = this.$fire.firestore
        .collection("gelen-mesajlar")
        .doc("dokuman-adi");
      try {
        await messageRef.set({
          mesaj: "Selam Dunya",
        });
      } catch (e) {
        alert(e);
        return;
      }
      alert("Success.");
    },
  },
};
</script>

<template>
  <div class="container">
    <a href="/kayit-ol">Kayit Ol</a>
    <a href="/giris-yap">Giris Yap</a>
  </div>
</template>

<style scoped>
.container {
  padding: 2rem;
  text-align: center;
}

a {
  border: none;
  color: white;
  padding: 15px 32px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
  margin: 4px 2px;
  cursor: pointer;
  background-color: #008cba;
}
</style>