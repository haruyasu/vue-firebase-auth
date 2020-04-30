<template>
  <v-app-bar app color="primary" dark>
    <v-toolbar-title>
      Vue Firebase Auth
    </v-toolbar-title>
    <v-spacer></v-spacer>
    <v-toolbar-items>
      <v-btn text v-if="!user" :to="{ name: 'Signup' }">
        サインアップ
      </v-btn>
      <v-btn text v-if="!user" :to="{ name: 'Login' }">
        ログイン
      </v-btn>
      <v-btn text v-if="user">
        {{ user.email }}
      </v-btn>
      <v-btn text v-if="user" @click="logout">
        ログアウト
      </v-btn>
    </v-toolbar-items>
  </v-app-bar>
</template>

<script>
import firebase from "firebase";
export default {
  name: "Navbar",
  data() {
    return {
      user: null
    };
  },
  created() {
    firebase.auth().onAuthStateChanged(user => {
      if (user) {
        this.user = user;
      } else {
        this.user = null;
      }
    });
  },
  methods: {
    logout() {
      firebase
        .auth()
        .signOut()
        .then(() => {
          this.$router.push({ name: "Login" });
        });
    }
  }
};
</script>
