<template>
  <v-app>
    <Navbar />
    <v-content>
      <v-container>
        <router-view />
      </v-container>
    </v-content>
    <v-footer app color="primary" dark class="justify-center">
      Vue Firebase Auth
    </v-footer>
  </v-app>
</template>

<script>
import Navbar from "@/components/Navbar";

export default {
  name: "App",

  components: {
    Navbar
  }
};
</script>
