<template>
  <v-layout column>
    <div>
      <v-toolbar flat dense color="grey darken-4">
        <v-toolbar-title>
          {{ title }}
        </v-toolbar-title>
        <slot name="action"></slot>
      </v-toolbar>

      <div class="pl-4 pr-4 pt-2 pb-2">
        <slot>
          No slot content defined.
        </slot>
      </div>
    </div>
  </v-layout>
</template>

<script>
export default {
  props: [
    'title'
  ]
}
</script>

<style>

</style>
