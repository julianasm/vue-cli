<template>
  <v-app>
    <v-app-bar app color="primary">
      <v-app-bar-title>Vue + Vuetify</v-app-bar-title>
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
    <!-- Login -->
    <v-main>
      <v-card width="500px" class="mx-auto mt-5">
      <v-card-title>
       <h1 class="display-1">Login</h1> 
      </v-card-title>
      <v-card-text>
        <v-form>
          <v-text-field 
          label="username"
          prepend-icon="mdi-account-circle"
          ></v-text-field>
          <v-text-field 
          label="password"
          prepend-icon="mdi-lock"
          :append-icon="exibir? 'mdi-eye' : 'mdi-eye-off'"
          :type="exibir ? ' text' : 'password'"
          @click:append="showHide"
          ></v-text-field>
        </v-form>
      </v-card-text>
    <v-card-actions>
      <v-btn color="success">
        Register
      </v-btn>
      <v-spacer></v-spacer>
      <v-btn color="info">
        Login
      </v-btn>
    </v-card-actions>
      </v-card>
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
    exibir: false,
    links: [
        'Home',
        'Login',
        'Cadastro'
      ],
  }),
  
  methods: {
        showHide() {
          this.exibir = !this.exibir
    },
  } 

  
};
</script>
