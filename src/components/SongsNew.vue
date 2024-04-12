<script>
export default {
  data: function () {
    return {
      newSongParams: {},
    };
  },
  methods: {
    handleSubmit: function () {
      this.$emit("createSong", this.newSongParams);
      this.newSongParams = {};
    },
  },
};
</script>

<template>
  <div>
    <h1>New Songs</h1>
    <form>
      <form v-on:submit.prevent="handleSubmit"></form>
      <div>
        Title:
        <input type="text" v-model="newSongParams.title" />
      </div>
      <div>
        Url:
        <input type="text" v-model="newSongParams.url" />
      </div>
      <div>
        Album:
        <input type="text" v-model="newSongParams.album" />
      </div>
      <div>
        Artist:
        <input type="text" v-model="newSongParams.artist" />
      </div>
      <button type="submit">Create song</button>
    </form>
  </div>
</template>

<style></style>
