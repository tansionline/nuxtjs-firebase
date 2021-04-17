<script>
export default {
  methods: {
    async firestoreYaz() {
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
      alert("Basarili.");
    },
  },
};
</script>

<template>
  <div class="container">
    <button v-on:click="firestoreYaz">Gonder</button>
  </div>
</template>

<style scoped>
.container {
  padding: 2rem;
  text-align: center;
}

button {
  border: none;
  color: white;
  padding: 15px 32px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
  margin: 4px 2px;
  cursor: pointer;
  background-color: #f44336;
}
</style>