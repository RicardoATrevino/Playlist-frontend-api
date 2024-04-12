<script>
export default {
  props: {
    songs: Array,
  },
};
</script>

<template>
  <div>
    <h1>All songs</h1>
    <div v-for="song in songs" v-bind:key="song.id">
      <h2>{{ song.name }}</h2>
      <img v-bind:src="song.url" />
      <p>URL: {{ song.url }}</p>
      <p>Title: {{ song.title }}</p>
      <p>Artist: {{ song.artist }}</p>
      <p>Album: {{ song.Album }}</p>
      <button v-on:click="$emit('showSong', song)">More info</button>
    </div>
  </div>
</template>

<style></style>
