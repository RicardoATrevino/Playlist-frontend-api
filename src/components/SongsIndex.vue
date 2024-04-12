<script>
export default {
  props: {
    songs: Array,
  },
};
</script>

<template>
  <div>
    <h1>All Songs</h1>
    <div v-for="song in songs" v-bind:key="song.id">
      <h2>{{ song.title }}</h2>
      <h4>by {{ song.artist }} || album: {{ song.album }}</h4>
      <h5 href="{{song.url}}">URL: {{ song.url }}</h5>
    </div>
  </div>
</template>

<style></style>
