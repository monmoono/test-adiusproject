<template>
  <v-app>
    <v-main>
      <v-row justify="center" class="container1">
        <v-col class="box1">
          <h1>Meet our leadership</h1>
          <p>
            Libero fames augue nisl porttitor nisi,quis. Id ac elit odio vitae
            elementum enim vitae ullamcorper suspendisse.Vivamus fringilla.
          </p>
        </v-col>
        <v-col class="box2">
          <v-list-item three-line v-for="(item, index) in items" :key="index">
            <template>
              <img
                :src="item.avatar"
                style="width: 75px; height: 75px; border-radius: 50%"
              />
            </template>
            <v-list-item-content>
              <h4>{{ item.first_name + " " + item.last_name }}</h4>
              <h5 class="emailtext">{{ item.email }}</h5>
            </v-list-item-content>
          </v-list-item>
        </v-col>
      </v-row>
      <!-- <v-container flat>
       
      </v-container> -->
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

<style lang="sass">
.box1
  grid-area: Box1
  width: 32rem

.box2
  display: grid
  grid-area: Box2
  grid-template-columns: auto auto


.container1
  display: grid
  grid-template-areas: "Box1 Box2 Box2 Box2 Box2"
  gap: 1rem
  padding: 1rem

.emailtext
  color: #3F51B5
</style>
