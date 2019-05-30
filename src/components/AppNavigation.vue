<template>
  <span>
    <v-navigation-drawer
      app
      v-model="drawer"
      class="blue darken-1"
      disable-resize-watcher
    >
      <v-list>
        <template v-for="(item, index) in items">
          <v-list-tile :key="index">
            <v-list-tile-content class="white--text">
              {{ item.title }}
            </v-list-tile-content>
          </v-list-tile>
          <v-divider :key="`divider-${index}`"></v-divider>
        </template>
      </v-list>
    </v-navigation-drawer>

    <v-toolbar app color="blue darken-1" dark>
      <v-toolbar-side-icon
        class="hidden-sm-and-up"
        @click="drawer = !drawer"
      ></v-toolbar-side-icon>
      <v-toolbar-title class="hidden-sm-and-up"
        ><v-icon left>local_cafe</v-icon>{{ appTitle }}</v-toolbar-title
      >
      <v-btn flat class="hidden-xs-only">
        <v-icon left>home</v-icon>
        Home
      </v-btn>
      <v-btn flat class="hidden-xs-only">
        <v-icon left>trending_up</v-icon>
        Best Sellers
      </v-btn>
      <v-btn flat class="hidden-xs-only">
        <v-icon left>contact_mail</v-icon>
        About
      </v-btn>
    </v-toolbar>
  </span>
</template>

<script>
export default {
  name: "AppNavigation",
  data() {
    return {
      appTitle: "mugtweet.club",
      drawer: false,
      items: [{ title: "Home" }, { title: "Best Sellers" }, { title: "About" }]
    };
  }
};
</script>

<style scoped></style>
