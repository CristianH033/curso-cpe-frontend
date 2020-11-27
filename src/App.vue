<template>
  <v-app>
    <v-app-bar app color="primary" dark>
      <v-app-bar-nav-icon></v-app-bar-nav-icon>
      <v-toolbar-title>Contratos CPE</v-toolbar-title>
    </v-app-bar>
    <v-main>
      <Productos />
    </v-main>
  </v-app>
</template>

<script>
import Productos from "./components/Productos";

export default {
  name: "App",

  components: {
    Productos,
  },

  data: () => ({
    //
  }),
};
</script>
