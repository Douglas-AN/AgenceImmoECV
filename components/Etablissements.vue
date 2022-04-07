<template>
  <div id="app">
    <div v-for="annonce in annonces" :key="annonce.id">
      <NuxtLink :to="'/' + annonce.id">{{
        annonce.attributes.Intitule
      }}</NuxtLink>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import Etablissements from "../components/Etablissements.vue";
export default {
  components: { Etablissements },
  name: "IndexPage",
  data() {
    return {
      annonces: [],
    };
  },
  async mounted() {
    const response = await axios({
      url: "http://localhost:1337/api/etablissements",
      method: "get",
    });
    this.annonces = response.data.data;
    console.log(response);
  },
};
</script>