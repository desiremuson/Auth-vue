<template>
  <v-app>
    <v-app-bar app dark>
      <v-toolbar>
        <v-app-bar-nav-icon @click="home"></v-app-bar-nav-icon>
        <v-toolbar-title>Desire Auth</v-toolbar-title>
        <v-spacer></v-spacer>

        <v-btn text @click="register">
          Register
        </v-btn>
        <v-btn text @click="login">
          Login
        </v-btn>
        
      </v-toolbar>
    </v-app-bar>

    <v-main>
      <!-- <HelloWorld/> -->
      <router-view />
    </v-main>
  </v-app>
</template>

<script>
export default {
  name: "App",

  components: {},

  data: () => ({
    //
  }),
  methods: {
    home() {
      this.$router.push("/");
    },
    register() {
      this.$router.push("/register");
    },
    login() {
      this.$router.push("/login");
    },
 
  },
};
</script>
