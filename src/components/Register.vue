<template>
  <v-app id="inspire">
    <v-main>
      <v-container fluid fill-height>
        <v-layout align-center justify-center>
          <v-flex xs12 sm8 md4>
            <v-card class="elevation-12">
              <v-toolbar dark color="dark">
                <v-toolbar-title>Register </v-toolbar-title>
              </v-toolbar>
              <v-card-text>
                <v-form @submit.prevent="register">
                  <v-text-field
                    prepend-icon="email"
                    v-model="email"
                    :rules="emailRules"
                    label="E-mail"
                    required
                  ></v-text-field>
                  <v-text-field
                    id="password"
                    prepend-icon="lock"
                    v-model="password"
                    label="Password"
                    type="password"
                  ></v-text-field>
                  <v-text-field
                    prepend-icon="person"
                    v-model="name"
                    label="First Name"
                    required
                  ></v-text-field>
                  <v-text-field
                    prepend-icon="person"
                    v-model="surname"
                    label="Surname"
                    required
                  ></v-text-field>
                  <v-text-field
                    prepend-icon="phone"
                    v-model="phone"
                    label="Phone"
                    required
                  ></v-text-field>
                  <v-text-field
                    prepend-icon="work"
                    v-model="companyName"
                    label="Company Name"
                    required
                  ></v-text-field>
                </v-form>
              </v-card-text>
              <v-card-actions>
                <v-spacer></v-spacer>
                <v-btn color="dark" @click="register">Register</v-btn>
              </v-card-actions>
            </v-card>
          </v-flex>
        </v-layout>
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
import axios from "axios";
export default {
  name: "Register",
  data() {
    return {
      name: "",
      surname: "",
      companyName: "",
      email: "",
      phone: "",
      password: "",

      emailRules: [
        (v) => !!v || "E-mail is required",
        (v) => /.+@.+\..+/.test(v) || "E-mail must be valid",
      ],
    };
  },
  methods: {
    async register() {
      await axios.post(
        "register",
        // {
        //   headers: {
        //     "X-Requested-With": "XMLHttpRequest",
        //     "Content-Type": "application/json",
        //   },
        // },
        {
          name: this.name,
          surname: this.surname,
          companyName: this.companyName,
          email: this.email,
          phone: this.phone,
          password: this.password,
          plainPassword: this.password,
        }
      );

      this.$router.push("/login");
    },
  },
};
</script>

<style></style>
