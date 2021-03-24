<template>
  <div class="home">
    <v-container
      id="contacts"
      class="fill-height fill-width"
      tag="section"
      fluid
    >
      <v-row align="center" justify="center">
        <v-col cols="12" sm="2">
          <div v-if="currentUser">
            <v-data-table
              :headers="headers"
              :items="allContacts"
              :items-per-page="10"
              class="elevation-1"
            ></v-data-table>
          </div>
          <h3 v-if="!currentUser">You are not logged in</h3>
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "Home",

  data() {
    return {
      allContacts: [],
      currentUser: null,
      headers: [
        {
          text: "First name",
          align: "start",
          sortable: true,
          value: "name",
        },
        { text: "Surname", value: "surname" },
        { text: "Email Address", value: "email" },
        { text: "Telephone", value: "phone" },
        { text: "Company", value: "companyName" },
      ],
    };
  },

  async created() {
    // const response = await axios.get("users");
    const response = await axios.get("contacts"
	//  {
    //   headers: {
    //     "X-Requested-With": "XMLHttpRequest",
    //     "Content-Type": "application/json",
    //     Authorization: `Bearer ${localStorage.setItem("token")}`,
    //     // Authorization: `Bearer ${token}`,
    //   },
    // }
	);
   this.$store.dispatch("user", response.data)

    const getAll = await axios.get("contacts", {
      headers: {
        "X-Requested-With": "XMLHttpRequest",
        "Content-Type": "application/json",
      },
    });
    this.allContacts = getAll.data;
  },
};
</script>
