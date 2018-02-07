<template>
  <panel title="Youtube Video" class="ml-2">
    <youtube
      :video-id="youtubeId"
      :player-width="700"
      :player-height="400">
    </youtube>
  </panel>
</template>

<script>
import Panel from '@/components/Panel'

export default {
  props: [
    'youtubeId'
  ],
  components: {
    Panel
  }
}
</script>

<style>

</style>
