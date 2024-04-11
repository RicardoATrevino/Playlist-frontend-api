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
      <h2>{{ song.name }}</h2>
      <img v-bind:src="song.url" />
      <p>Width: {{ song.width }}</p>
      <p>Height: {{ song.height }}</p>
    </div>
  </div>
</template>

<style></style>
