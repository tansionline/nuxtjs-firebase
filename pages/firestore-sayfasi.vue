<script>
export default {
  data() {
    return {
      mesaj: "",
    };
  },

  methods: {
    async firestoreOku() {
      const messageRef = this.$fire.firestore
        .collection("gelen-mesajlar")
        .doc("dokuman-adi");
      try {
        const messageDoc = await messageRef.get();
        alert(messageDoc.data().mesaj);
      } catch (e) {
        alert(e);
        return;
      }
    },
    async firestoreYazdir() {
      const messageRef = this.$fire.firestore
        .collection("gelen-mesajlar")
        .doc("dokuman-adi");
      try {
        await messageRef.set({
          mesaj: this.mesaj,
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
    <form @submit.prevent="firestoreYazdir">
      <textarea v-model="mesaj"></textarea>
      <button type="submit">Gonder</button>
    </form>
    <button v-on:click="firestoreOku">Firestore Okuma</button>
  </div>
</template>

<style scoped>
.container {
  padding: 2rem;
  text-align: center;
}

textarea {
  width: 100%;
  height: 150px;
  padding: 12px 20px;
  box-sizing: border-box;
  border: 2px solid #ccc;
  border-radius: 4px;
  background-color: #f8f8f8;
  font-size: 16px;
  resize: none;
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