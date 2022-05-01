<template>
  <v-app>
    <v-app-bar
      app
      color="dark"
      dark
      elevation="0"
    >
      <div class="d-flex align-center">
        <v-img
          alt="Vuetify Logo"
          class="shrink mr-2"
          contain
          src="https://cdn.vuetifyjs.com/images/logos/vuetify-logo-dark.png"
          transition="scale-transition"
          width="40"
        />

   
      </div>

      <v-spacer></v-spacer>

      <v-btn
        href="#"
        target="_blank"
        text
      >
        <span class="mr-2">Login</span>
        <v-icon size="20px">mdi-open-in-new</v-icon>
      </v-btn>

      <v-btn
        href="#"
        target="_blank"
        text
         >
        <span class="mr-2">Logout</span>
        <v-icon size="20px">mdi-open-in-new</v-icon>
      </v-btn>
    </v-app-bar>

    <v-main>
      <HelloWorld/>
    </v-main>
  </v-app>
</template>

<script>
import HelloWorld from './components/HelloWorld';

export default {
  name: 'App',

  components: {
    HelloWorld,
  },

  data: () => ({
    //
  }),
};
</script>
