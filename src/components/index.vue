<template>
  <v-app>
    <v-main class="com">
      <h1 class="welcome mainsitecolor">Welcome to website</h1>
      <v-container flat>
        <v-row no-gutters class="container1">
          <v-col class="box1">
            <h1 class="text-h">Meet our leadership</h1>
            <p class="textp">
              Libero fames augue nisl porttitor nisi,quis. Id ac elit odio vitae
              elementum enim vitae ullamcorper suspendisse.Vivamus fringilla.
            </p>
          </v-col>
          <v-col class="box2 list-head">
            <v-list-item
              three-line
              v-for="(item, index) in items"
              :key="index"
              class="list-list"
            >
              <template>
                <img class="list-img" :src="item.avatar" />
              </template>
              <v-list-item-content>
                <v-list-item-title class="list-name">{{
                  item.first_name + " " + item.last_name
                }}</v-list-item-title>
                <v-list-item-subtitle class="list-email">{{
                  item.email
                }}</v-list-item-subtitle>
              </v-list-item-content>
            </v-list-item>
          </v-col>
        </v-row>
      </v-container>
    </v-main>
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
      this.items = arr;
      console.log(arr);
    });
  },
};
</script>

<style lang="sass">
@import './src/assets/button.sass'
.box1
  grid-area: Box1

.box2
  display: grid
  grid-area: Box2
  grid-template-columns: auto auto

.container1
  display: grid
  grid-template-areas: "Box1 Box2 Box2"
  gap: 1rem
  padding: 7% auto

.textp
  line-height: 1.5
  padding-top: 1.5rem
  font-size: 1.5rem

.text-h
  font-size: 3.5rem

.list-name
  padding-left: 15px
  font-size: 1.5rem

.list-email
  padding-left: 15px
  font-size: 1rem

.list-head
  margin-left: 10%


.list-img
  width: 85px
  height: 85px
  border-radius: 50%

.com
  margin-top: 8%

.welcome
  text-align: center
  font-size: 4rem
  margin-bottom: 3%
  color: #FFF
  margin-left: 30rem
  margin-right: 30rem
  border-radius: 1.5rem
</style>
