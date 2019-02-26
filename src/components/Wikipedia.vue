

<template>
  <v-container>
    <v-card>
      <v-card-title class="headline font-weight-regular blue-grey white--text">Votre recherche</v-card-title>
      <v-card-text>
        <v-subheader class="pa-0">Quelle est votre recherche ?</v-subheader>
        <v-autocomplete
          :items="items"
          :search-input.sync="search"
          v-model="searchInput"
          flat
          label="Recherche"
          persistent-hint
          prepend-icon="mdi-city"
        ></v-autocomplete>
      </v-card-text>
    </v-card>
  </v-container>
</template>

<script>
export default {
  data() {
    return {
      searchInput: null,
      items: [],
      search: null,
      select: null
    };
  },
  watch: {
    search: "getProposition"
  },
  methods: {
    async getProposition(word) {
      const axios = require("axios");

      axios
        .get(
          "https://cors.io/?https://en.wikipedia.org/w/api.php?action=opensearch&search=" +
            word +
            "&namespace=0&format=json"
        )
        .then(function(response) {
          console.log(response);
          this.items = response[1];
        })
        .catch(function(error) {
          // handle error
          console.log(error);
        })
        .then(function() {
          // always executed
        });
    }
  }
};
</script>

<style>
</style>
