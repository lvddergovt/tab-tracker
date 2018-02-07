<template>
  <div>
    <v-layout>
      <v-flex sm6>
        <song-metadata :song="song"></song-metadata>
      </v-flex>
      <v-flex sm6>
        <you-tube :youtubeId="song.youtubeId"></you-tube>
      </v-flex>
    </v-layout>

    <v-layout>
      <v-flex sm6>
        <lyrics :song="song"></lyrics>
      </v-flex>
      <v-flex sm6>
        <tab :song="song"></tab>
      </v-flex>
    </v-layout>
    <!-- <v-layout>
      <v-flex sm6>
        <panel title="tabs">
          <textarea readonly v-model="song.tab"></textarea>
        </panel>
      </v-flex>
      <v-flex sm6>
       
      </v-flex>
    </v-layout> -->
  </div>
</template>

<script>
import Lyrics from './Lyrics'
import Panel from '@/components/Panel'
import SongMetadata from './SongMetadata'
import SongsService from '@/services/SongsService'
import Tab from './Tab'
import YouTube from './Youtube'

export default {
  data () {
    return {
      song: {}
    }
  },
  async mounted () {
    const songId = this.$store.state.route.params.songId
    this.song = (await SongsService.show(songId)).data
  },
  components: {
    Panel,
    SongMetadata,
    YouTube,
    Lyrics,
    Tab
  }
}
</script>

<style scoped>

</style>
