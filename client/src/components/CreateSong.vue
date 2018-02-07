<template>
  <v-layout>
    <v-flex>
      <panel title="Song Metadata" xs12 sm4>
        <v-text-field type="text" required :rules="[required]" label="Title" v-model="song.title" color="teal lighten-4"></v-text-field>
        <v-text-field type="text" required :rules="[required]" label="Artist" v-model="song.artist" color="teal lighten-4"></v-text-field>
        <v-text-field type="text" required :rules="[required]" label="Genre" v-model="song.genre" color="teal lighten-4"></v-text-field>
        <v-text-field type="text" required :rules="[required]" label="Album" v-model="song.album" color="teal lighten-4"></v-text-field>
        <v-text-field type="text" required :rules="[required]" label="Album Image Url" v-model="song.albumImageUrl" color="teal lighten-4"></v-text-field>
        <v-text-field type="text" required :rules="[required]" label="Youtube ID" v-model="song.youtubeId" color="teal lighten-4"></v-text-field>
      </panel>
    </v-flex>
    <v-flex xs12 sm7 offset-sm1>
      <panel title="Song Structure">
        <v-text-field type="text" required :rules="[required]" label="Tab" multi-line v-model="song.tab" color="teal lighten-4"></v-text-field>
        <v-text-field type="text" required :rules="[required]" label="Lyrics" multi-line v-model="song.lyrics" color="teal lighten-4"></v-text-field>
      </panel>
      <div class="danger-alert" v-if="error">
        {{ error }}
      </div>
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
      },
      error: null,
      required: (value) => !!value || 'Required.'
    }
  },
  methods: {
    async create () {
      this.error = null
      const areAllFieldsFilledIn = Object.keys(this.song).every(key => !!this.song[key])
      if (!areAllFieldsFilledIn) {
        this.error = 'Please fill in all the required fields.'
        return
      }
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
