<template>
  <panel title="Tab" class="ml-2">
    <textarea readonly v-model="song.tab"></textarea>
  </panel>
</template>

<script>
import Panel from '@/components/Panel'

export default {
  props: [
    'song'
  ],
  components: {
    Panel
  }
}
</script>

<style scoped>
textarea {
  width: 100%;
  font-family: monospace;
  font-size: 12px;
  border: none;
  height: 600px;
  overflow: auto;
  padding: 40px;
}
</style>
