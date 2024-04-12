<script>
export default {
  props: {
    song: Object,
  },
  data: function () {
    return {
      editSongsParams: {},
    };
  },
  created: function () {
    this.editSongParams = { ...this.song };
  },
  methods: {
    handleSubmit: function () {
      this.$emit("updateSong", this.song.id, this.editSongParams);
    },
  },
};
</script>

<template>
  <div>
    <h1>Song information</h1>
    <p>Name: {{ song.name }}</p>
    <p>Url: {{ song.url }}</p>
    <p>Width: {{ song.width }}</p>
    <p>Height: {{ song.height }}</p>
    <form v-on:submit.prevent="handleSubmit">
      <div>
        Name:
        <input v-model="editSongParams.name" type="text" />
      </div>
      <div>
        Url:
        <input v-model="editSongParams.url" type="text" />
      </div>
      <div>
        Width:
        <input v-model="editSongParams.width" type="text" />
      </div>
      <div>
        Height:
        <input v-model="editSongParams.height" type="text" />
      </div>
      <button v-on:click="$emit('destroySong', song)">Destroy song</button>
    </form>
  </div>
</template>

<style></style>
