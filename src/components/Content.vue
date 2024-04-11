<script>
import axios from "axios";
import SongsIndex from "./SongsIndex.vue";
export default {
  components: {
    SongsIndex,
  },
  data: function () {
    return {
      songs: [
        { id: 1, name: "First", url: "https://via.placeholder.com/150", width: 150, height: 150 },
        { id: 2, name: "Second", url: "https://via.placeholder.com/300", width: 300, height: 300 },
      ],
    };
  },
  created: function () {
    this.handleIndexSongs();
  },
  methods: {
    handleIndexSongs: function () {
      axios.get("http://localhost:3000/songs.json").then((response) => {
        console.log("songs index", response);
        this.songs = response.data;
      });
    },
  },
};
</script>

<template>
  <main>
    <SongsIndex />
    <SongsIndex v-bind:songs="songs" />
  </main>
</template>

<style></style>
