<script>
import axios from "axios";
import SongsIndex from "./SongsIndex.vue";
import SongsNew from "./SongsNew.vue";
import SongsShow from "./SongsShow.vue";
import Modal from "./Modal.vue";

export default {
  components: {
    SongsIndex,
    SongsNew,
    SongsShow,
    Modal,
  },
  data: function () {
    return {
      songs: [],
      currentSong: {},
      isSongsShowVisible: false,
    };
  },
  created: function () {
    this.handleIndexSongs();
  },
  methods: {
    handleIndexSongs: function () {
      axios.get("http://localhost:5000/songs.json").then((response) => {
        console.log("songs index", response);
        this.songs = response.data;
      });
    },
    handleCreateSong: function (params) {
      axios
        .post("http://localhost:5000/songs.json", params)
        .then((response) => {
          console.log("songs create", response);
          this.songs.push(response.data);
        })
        .catch((error) => {
          console.log("songs create error", error.response);
        });
    },
    handleShowSong: function (song) {
      console.log("handleShowSong", song);
      this.currentSong = song;
      this.isSongsShowVisible = true;
    },
    handleUpdateSong: function (id, params) {
      console.log("handleUpdateSong", id, params);
      axios
        .patch(`http://localhost:5000/songs/${id}.json`, params)
        .then((response) => {
          console.log("songs update", response);
          this.songs = this.songs.map((song) => {
            if (song.id === response.data.id) {
              return response.data;
            } else {
              return song;
            }
          });
          this.handleClose();
        })
        .catch((error) => {
          console.log("songs update error", error.response);
        });
    },
    handleDestroySong: function (song) {
      axios.delete(`http://localhost:5000/songs/${song.id}.json`).then((response) => {
        console.log("songs destroy", response);
        var index = this.songs.indexOf(song);
        this.songs.splice(index, 1);
        this.handleClose();
      });
    },
    handleClose: function () {
      this.isSongsShowVisible = false;
    },
  },
};
</script>

<template>
  <main>
    <SongsNew v-on:createSong="handleCreateSong" />
    <SongsIndex v-bind:songs="songs" v-on:showSong="handleShowSong" />
    <Modal v-bind:show="isSongsShowVisible" v-on:close="handleClose">
      <h1>Test</h1>
      <SongsShow v-bind:song="currenSong" v-on:updateSong="handleUpdateSong" v-on:destroySong="handleDestroySong" />
    </Modal>
  </main>
</template>

<style></style>
