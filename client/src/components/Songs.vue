<template>
  <v-flex sm10 md6 offset-sm1 offset-md3>
    <panel title="Songs">
      <div v-for="song in songs" :key="song.id">
        {{ song.title }} -
        {{ song.artist }} -
        {{ song.album }}
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
  async mounted () {
    this.songs = (await SongsService.index()).data
  }
}
</script>

<style scoped>

</style>
