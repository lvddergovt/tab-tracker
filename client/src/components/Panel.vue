<template>
  <v-layout column>
    <v-flex sm6 offset-sm3>
      <div>
        <v-toolbar flat dense color="grey darken-4">
          <v-toolbar-title>
            {{ title }}
          </v-toolbar-title>
        </v-toolbar>

        <div class="pl-4 pr-4 pt-2 pb-2">
          <slot>
            No slot content defined.
          </slot>
        </div>
      </div>
    </v-flex>
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
