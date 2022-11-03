<template>
  <v-app>
    <div id="navbar">
      <v-app-bar color="deep-purple" dark>
        <v-app-bar-nav-icon
          @click="drawer = true"
          class="d-flex d-sm-none"
        ></v-app-bar-nav-icon>

        <v-img
          alt="Vuetify Name"
          class="shrink mt-1"
          contain
          min-width="100"
          src="@/assets/logo2.png"
          width="150"
        />

        <v-menu offset-y open-on-hover :close-on-content-click="true">
          <template v-slot:activator="{ on, attrs }">
            <v-btn color="blue lighten-2" class="mx-2"> Sign up </v-btn>
            <v-btn color="lighten-0" class="mx-2"> sign in </v-btn>
            <v-spacer></v-spacer>
            <v-btn color="blue lighten-2" class="mx-2"> Docs </v-btn>
            <v-btn color="blue lighten-2" class="mx-2"> Pricing </v-btn>
            <v-btn
              color="blue lighten-2"
              v-bind="attrs"
              v-on="on"
              class="dropdown mx-2"
            >
              Solutions
              <v-icon>mdi-chevron-down </v-icon>
            </v-btn>
          </template>
          <div>
            <div class="grid-container">
              <div class="grid-item">
                <v-list-item
                  three-line
                  v-for="(item, index) in itemsL"
                  :key="index"
                  link
                >
                  <v-list-item-icon
                    ><v-icon color="blue lighten-2">{{
                      item.icon
                    }}</v-icon></v-list-item-icon
                  >
                  <v-list-item-content>
                    <v-list-item-title>{{ item.title }}</v-list-item-title>
                    <v-list-item-subtitle>{{ item.a }}</v-list-item-subtitle>
                  </v-list-item-content>
                </v-list-item>
              </div>
              <div class="grid-item">
                <v-list-item
                  three-line
                  v-for="(item, index) in itemsR"
                  :key="index"
                  link
                >
                  <v-list-item-icon
                    ><v-icon color="blue lighten-2">{{
                      item.icon
                    }}</v-icon></v-list-item-icon
                  >
                  <v-list-item-content>
                    <v-list-item-title>{{ item.title }}</v-list-item-title>
                    <v-list-item-subtitle>{{ item.a }}</v-list-item-subtitle>
                  </v-list-item-content>
                </v-list-item>
              </div>
              <div class="grid-button">
                <v-list-item two-line>
                  <v-list-item-content>
                    <v-list-item-title
                      >Emterprise<v-icon color="blue lighten-2" large
                        >mdi-new-box
                      </v-icon></v-list-item-title
                    >
                    <v-list-item-subtitle
                      >Emterprise your entire team with even more advanced
                      tools.</v-list-item-subtitle
                    >
                  </v-list-item-content>
                </v-list-item>
              </div>
            </div>
          </div>
        </v-menu>
      </v-app-bar>
      <v-spacer></v-spacer>

      <!-- nav when responsive -->
      <v-navigation-drawer v-model="drawer" absolute temporary>
        <v-list nav dense>
          <v-list-item-group
            v-model="group"
            active-class="deep-purple--text text--accent-4"
          >
            <v-list-item>
              <v-list-item-icon>
                <v-icon>mdi-home</v-icon>
              </v-list-item-icon>
              <v-list-item-title>Home</v-list-item-title>
            </v-list-item>

            <v-list-item>
              <v-list-item-icon>
                <v-icon>mdi-account</v-icon>
              </v-list-item-icon>
              <v-list-item-title>Account</v-list-item-title>
            </v-list-item>
          </v-list-item-group>
        </v-list>
      </v-navigation-drawer>
    </div>

    <v-main>
      <router-view />
    </v-main>

    <v-footer dark padless>
      <v-card class="flex" flat tile>
        <v-card-title class="deep-purple">
          <v-row no-gutters>
            <v-col cols="4" sm="4">
              <strong class="subheading"
                >Get connected with us on social networks!</strong
              >
              <v-divider></v-divider>
              <v-btn v-for="icon in icons" :key="icon" class="mx-4" dark icon>
                <v-icon size="24px">
                  {{ icon }}
                </v-icon>
              </v-btn>
            </v-col>
            <!-- <v-col cols="2" sm="2">
              <strong class="subheading">solution</strong>
              <v-list-item >
                <v-list-item-content>
                  <a href="">Two-line item</a>
                </v-list-item-content>
              </v-list-item>
            </v-col>
             <v-col cols="2" sm="2">
              <strong class="subheading">solution</strong>
              <v-list-item >
                <v-list-item-content>
                  <a href="">Two-line item</a>
                </v-list-item-content>
              </v-list-item>
            </v-col>
             <v-col cols="2" sm="2">
              <strong class="subheading">solution</strong>
              <v-list-item >
                <v-list-item-content>
                  <a href="">Two-line item</a>
                </v-list-item-content>
              </v-list-item>
            </v-col>
             <v-col cols="2" sm="2">
              <strong class="subheading">solution</strong>
              <v-list-item >
                <v-list-item-content>
                  <a href="">Two-line item</a>
                </v-list-item-content>
              </v-list-item>
            </v-col>             -->
          </v-row>
        </v-card-title>

        <!-- <v-card-text class="py-2 white--text text-center"><strong>Years</strong>
        {{ new Date().getFullYear() }} — <strong>Vuetify</strong>
      </v-card-text> -->
      </v-card>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  name: "App",
  data: () => ({
    itemsL: [
      {
        title: "Analytics",
        a: "Get a better understanding of where your traffic is coming from.",
        icon: "mdi-google-analytics ",
      },
      {
        title: "Securlity",
        a: "Your customers data will be safe and secure.",
        icon: "mdi-shield-account ",
      },
      {
        title: "Automations",
        a: "Build strategic funnels that will drive your customers to convert.",
        icon: "mdi-autorenew ",
      },
    ],
    itemsR: [
      {
        title: "Engagement",
        a: "Speak directly to your customers in a more meaningful way.",
        icon: "mdi-cursor-default-click",
      },
      {
        title: "Integrations",
        a: "Connect with third-party tools that you're already using.",
        icon: "mdi-view-grid",
      },
      {
        title: "Report",
        a: "Get detailed reports that will help you make more inforned decisions",
        icon: "mdi-file-chart ",
      },
    ],
    icons: ["mdi-facebook", "mdi-twitter", "mdi-linkedin", "mdi-instagram"],
  }),
  methods: {
    Logout() {
      this.$router.push({ name: "HomeView" });
    },
  },
};
</script>

<style lang="sass" scoped>
.grid-container
  background-color: rgba(240, 240, 240, 1)
  // display: grid
  column-count: 2
  max-width: 50rem
  // grid-template-columns: auto auto
  // background-color: #2196F3
  padding: 10px

.grid-item
  background-color: rgba(240, 240, 240, 1)
  // border: 1px solid rgba(0, 0, 0, 0.8)
  padding: 20px
  font-size: 30px
  // text-align: center
  column-span: 1

.grid-button
  background-color: rgba(220, 220, 220, 1)
  // border: 1px solid rgba(0, 0, 0, 0.8)
  padding: 20px
  font-size: 30px
  column-span: all
</style>
