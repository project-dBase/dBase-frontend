<template>
    <v-app-bar app color="primary" class="colorOFfont" >

      <v-img
        src="@/public/logoHeader.png"
        alt="Logo"
        max-width="40"
        max-height="40"
        class="mx-2"
      ></v-img>

      <v-toolbar-title>
        dBase
      </v-toolbar-title>

      <v-app-bar-nav-icon @click="toggleDrawer">
        <v-icon>mdi-menu</v-icon>
      </v-app-bar-nav-icon>
    </v-app-bar>

    <v-navigation-drawer app v-model="drawer" right color="secondary" class="colorOFfont">
      <v-list>
        <v-list-item-group>
          <v-list-item @click="selectCategory('verify')">

            <v-list-item-content>
                <nuxt-link to="/test">Test</nuxt-link>
              <v-list-item-title>Verify your database</v-list-item-title>
            </v-list-item-content>
          </v-list-item>

          <v-list-item @click="selectCategory('getData')">

            <v-list-item-content>
              <v-list-item-title>Get needed data</v-list-item-title>
            </v-list-item-content>
          </v-list-item>

          <v-list-item @click="selectCategory('statistics')">

            <v-list-item-content>
              <v-list-item-title>Get needed statistics</v-list-item-title>
            </v-list-item-content>
          </v-list-item>
        </v-list-item-group>
      </v-list>
    </v-navigation-drawer>
</template>

<script>
export default {
  name: "AppBar",
  data() {
    return {
      drawer: false,
    };
  },
  methods: {
    toggleDrawer() {
      this.drawer = !this.drawer;
    },
    selectCategory(category) {
      console.log(`Odabrana kategorija: ${category}`);
    },
  },
}
</script>

<style scoped>

.colorOFfont {
  color: #D7C3CE !important;
}
</style>
