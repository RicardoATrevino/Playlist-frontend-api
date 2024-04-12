<script>
import axios from "axios";
import SongsIndex from "./SongsIndex.vue";
import "../style.css";
export default {
  components: {
    SongsIndex,
  },
  data: function () {
    return {
      songs: [],
    };
  },
  created: function () {
    this.handleIndexSongs();
  },
  methods: {
    handleIndexSongs: function () {
      axios
        .get("http://localhost:5000/songs.json")
        .then((response) => {
          console.log("songs index", response);
          this.songs = response.data;
        })
        .catch((error) => {
          console.error("error fetching songs:", error);
        });
    },
  },
};
</script>

<template>
  <main>
    <SongsIndex v-bind:songs="songs" :class="songs" />
  </main>
</template>

<style></style>
