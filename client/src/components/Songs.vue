<template>
  <v-flex sm10 md6 offset-sm1 offset-md3 text-lg-center>
    <panel title="Songs">
      <v-btn class="green" absolute right middle slot="action" @click="navigateTo({name: 'songs-create'})">
        <v-icon>add</v-icon>
      </v-btn>
      <div v-for="song in songs" class="song" :key="song.id">

        <v-layout>
          <v-flex sm-6>
            <div class="song-title">
              {{ song.title }}
            </div>
            <div class="song-artist">
              {{ song.artist }}
            </div>
            <div class="song-genre">
              {{ song.genre }}
            </div>
            <v-btn color="teal lighten-2" @click="navigateTo({name: 'song', params: {songId: song.id}})" light>
            View
            </v-btn>
          </v-flex>
          <v-flex sm-6>
            <img class="album-image" :src="song.albumImageUrl">
          </v-flex>
        </v-layout>
      </div>
    </panel>
  </v-flex>
</template>

<script>
import Panel from '@/components/Panel'
import SongsService from '@/services/SongsService'
export default {
  components: {
    Panel
  },
  data () {
    return {
      songs: null
    }
  },
  methods: {
    navigateTo (route) {
      this.$router.push(route)
    }
  },
  async mounted () {
    this.songs = (await SongsService.index()).data
  }
}
</script>

<style scoped>
.song {
  padding: 20px;
  height: 200px;
  overflow: hidden;
}
.song-title {
  font-size: 30px;
}

.song-artist {
  font-size: 24px;
}

.song-genre {
  font-size: 18px;
}

.album-image {
  width: 150px;
  margin: 0 auto;
}
</style>
