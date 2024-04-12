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
      <h2>{{ song.artist }}</h2>
      <!-- <body>
        {{ song.album }}
        {{ song.url }}
      </body> -->
    </div>
  </div>
</template>

<style></style>
