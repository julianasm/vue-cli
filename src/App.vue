<template>
  <v-app>
    <v-app-bar app color="primary">
      <v-app-bar-title>Trainee</v-app-bar-title>
      <v-spacer></v-spacer>
      <v-btn
        v-for="link in links"
        :key="link"
        color="white"
        text
        rounded
        class="my-2"
      >
        {{ link }}
      </v-btn>
    </v-app-bar>
    <v-main>
      <router-view>
      </router-view>
    </v-main>
    <v-footer
      color="primary lighten-1"
      padless
    >
      <v-row
        justify="center"
        no-gutters
      >
      <v-btn
        v-for="link in links"
        :key="link"
        color="white"
        text
        rounded
        class="my-2"
      >
        {{ link }}
      </v-btn>
      <v-col
        class="primary lighten-2 py-6 text-center white--text"
        cols="12"
      >
        {{ new Date().getFullYear() }} — <strong>Vuetify</strong>
      </v-col>
    </v-row>
  </v-footer>
  </v-app>
</template>

<script>

export default {
  name: 'App',

  components: {
  },

  data: () => ({
      links: [
          'Home',
          'Login',
          'Cadastro'
        ],
    }),

  
};
</script>
