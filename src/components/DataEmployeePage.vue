<template>
  <v-container class="fill-height" fluid>
    <v-row align="center" justify="center" dense>
      <v-col
        cols="12"
        sm="8"
        md="4"
        lg="3"
        v-for="(item, index) in items"
        :key="index"
      >
        <v-card class="mx-auto" align="center" max-width="400" width="300">
          <div style="">
            <v-img :src="item.avatar" width="100" class="imgcircle"> </v-img>
          </div>

          <v-card-text>
            <h3>{{ item.first_name + " " + item.last_name }}</h3>
            <h5>{{ item.email }}</h5>
          </v-card-text>

          <v-card-actions>
            <v-btn color="grey lighten-0" text
              ><v-icon>mdi-email </v-icon>Email
            </v-btn>
            <v-spacer></v-spacer>
            <v-btn color="grey lighten-0" text
              ><v-icon>mdi-phone </v-icon>Call
            </v-btn>
          </v-card-actions>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
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
      //Show data by sort the characters in a string alphabetically
      arr.sort((a, b) => {
        const nameA = a.first_name.toUpperCase(); 
        const nameB = b.first_name.toUpperCase(); 
        if (nameA < nameB) {
          return -1;
        }
        if (nameA > nameB) {
          return 1;
        }
        // names must be equal
        return 0;
      });
      this.items = arr;
      console.log(arr);
    });
  },
  methods: {},
};
</script>

<style lang="sass" scoped>
.imgcircle
    border-radius: 50%

h3
    color: black
</style>
