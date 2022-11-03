<template>
  <v-app>
    <v-main>
      <v-container flat>
        <v-row no-gutters>
          <v-col cols="3" sm="3">
            <h1>Meet our leadership</h1>
            <p>
              Libero fames augue nisl porttitor nisi,quis. Id ac elit odio vitae
              elementum enim vitae ullamcorper suspendisse.Vivamus fringilla.
            </p>
          </v-col>

          <v-col cols="4" sm="3" lg="2">
            <v-card
              three-line
              v-for="(item, index) in items"
              :key="index"
              width="400px"
            >
              <img
                :src="item.avatar"
                style="width: 75px; height: 75px; border-radius: 50%"
              />
              <h4>{{ item.first_name + " " + item.last_name }}</h4>
              <h8>{{ item.email }}</h8>
              <!-- <v-list-item-content class="mx-3">
                <v-list-item-title>{{
                  item.first_name + " " + item.last_name
                }}</v-list-item-title>
                <v-list-item-subtitle>{{ item.email }}</v-list-item-subtitle>
              </v-list-item-content> -->
            </v-card>
          </v-col>
        </v-row>
      </v-container>
    </v-main>
    <!-- <v-card class="flex" flat tile>
      <v-card-title> </v-card-title>
    </v-card> -->
  </v-app>
</template>

<script>
import axios from "axios";
export default {
  name: "App",
  data: () => ({
    items: [],
  }),
  created() {
    axios.get("https://reqres.in/api/users").then((resp) => {
      let lg = resp.data.data;
      var arr = [];
      for (let i = 0; i < lg.length; i++) {
        var obj = {};
        obj = {
          id: resp.data.data[i].id,
          email: resp.data.data[i].email,
          first_name: resp.data.data[i].first_name,
          last_name: resp.data.data[i].last_name,
          avatar: resp.data.data[i].avatar,
        };
        arr.push(obj);
      }
      //this.datatable = arr;
      this.items = arr;
      console.log(arr);
    });
  },
  methods: {},
};
</script>
