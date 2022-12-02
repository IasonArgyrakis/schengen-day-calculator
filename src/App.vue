<template>
  <v-app>
    <v-app-bar
      app
      color="primary"
      dark
    >
      <div class="d-flex align-center">
        <v-img
          alt="Vuetify Logo"
          class="shrink mr-2"
          contain
          src="https://upload.wikimedia.org/wikipedia/commons/thumb/b/b7/Flag_of_Europe.svg/1599px-Flag_of_Europe.svg.png?20081021155534"
          transition="scale-transition"
          width="40"
        />

        <h2>Schengen Day Calculator</h2>
      </div>

      <v-spacer></v-spacer>

      <v-btn
        href="https://github.com/IasonArgyrakis"
        target="_blank"
        text
      >
        <span class="mr-2">Created By Iason Argyrakis</span>
        <v-icon>mdi-github</v-icon>
      </v-btn>
    </v-app-bar>

    <v-main>
      <router-view/>
    </v-main>
  </v-app>
</template>

<script>

export default {
  name: 'App',

  data: () => ({
    //
  }),
};
</script>
