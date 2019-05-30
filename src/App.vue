<template>
  <v-app>
    <v-toolbar app fixed clipped-left color="black" dark>
      <v-toolbar-title class="display-1 text-uppercase ml-0">
        <img width="37" height="37" src="logo.svg" />
        <span>Summit</span>
        <span class="font-weight-light">Grand prix</span>
      </v-toolbar-title>
    </v-toolbar>
    <v-container grid-list-xl text-xs-center>
      <v-layout row wrap>
        <v-content>
          <router-view></router-view>
        </v-content>
      </v-layout>
    </v-container>
  </v-app>
</template>

<script>
export default {
  name: 'App',
  props: {
    source: {
      type: String,
      default: ''
    }
  }
}
</script>
