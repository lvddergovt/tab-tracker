<template>
  <v-layout>
    <v-flex sm4>
      <panel title="Song Metadata">
        <v-text-field type="text" label="Title" v-model="song.title" color="teal lighten-4"></v-text-field>
        <v-text-field type="text" label="Artist" v-model="song.artist" color="teal lighten-4"></v-text-field>
        <v-text-field type="text" label="Genre" v-model="song.genre" color="teal lighten-4"></v-text-field>
        <v-text-field type="text" label="Album" v-model="song.album" color="teal lighten-4"></v-text-field>
        <v-text-field type="text" label="Album Image Url" v-model="song.albumImageUrl" color="teal lighten-4"></v-text-field>
        <v-text-field type="text" label="Youtube ID" v-model="song.youtubeId" color="teal lighten-4"></v-text-field>
      </panel>
    </v-flex>
    <v-flex sm7 offset-sm1>
      <panel title="Song Structure">
        <v-text-field type="text" label="Tab" multi-line v-model="song.tab" color="teal lighten-4"></v-text-field>
        <v-text-field type="text" label="Lyrics" multi-line v-model="song.lyrics" color="teal lighten-4"></v-text-field>
      </panel>
      <v-btn color="teal lighten-2" type="submit" @click="create" light>
        Create Song
      </v-btn>
    </v-flex>
  </v-layout>
</template>

<script>
import Panel from '@/components/Panel'
import SongsService from '@/services/SongsService'
export default {
  data () {
    return {
      song: {
        title: null,
        artist: null,
        genre: null,
        album: null,
        albumImageUrl: null,
        youtubeId: null,
        lyrics: null,
        tab: null
      }
    }
  },
  methods: {
    async create () {
      try { 
        await SongsService.post(this.song)
        this.$router.push({
          name: 'songs'
        })
      } catch (err) {
        console.log(err)
      }
    }
  },
  components: {
    Panel
  }
}
</script>

<style scoped>

</style>
