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
            <v-btn color="lighten-0" class="mx-2" @click="GotoLogin">
              sign in
            </v-btn>
            <v-spacer></v-spacer>
            <v-btn
              color="blue lighten-2"
              class="mx-2"
              href="https://vuetifyjs.com/en/introduction/why-vuetify/"
            >
              Docs
            </v-btn>
            <v-btn
              color="blue lighten-2"
              class="mx-2"
              href="https://www.google.com/"
            >
              Pricing
            </v-btn>
            <v-btn color="blue lighten-2" v-bind="attrs" v-on="on" class="mx-2">
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
              <div class="grid-buttom">
                <v-list-item two-line link>
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
    </div>

    <v-main>
      <router-view />
    </v-main>

    <v-footer dark padless>
      <v-card class="flex" flat tile>
        <v-card-title class="deep-purple">
          <v-row no-gutters>
            <v-col cols="1" sm="1">
              <v-img
                class="shrink mt-1"
                contain
                min-width="90"
                src="@/assets/logo.png"
                width="90"
              />
            </v-col>
            <v-col cols="2" sm="2">
              <v-list-item link
                ><v-list-item-content>
                  <v-list-item-title>Products</v-list-item-title>
                </v-list-item-content></v-list-item
              >
              <v-list-item v-for="(item, index) in itemsFt1" :key="index" link>
                <v-list-item-content>
                  <v-list-item-subtitle>{{ item.title }}</v-list-item-subtitle>
                </v-list-item-content>
              </v-list-item>
            </v-col>
            <v-col cols="2" sm="2">
              <v-list-item link
                ><v-list-item-content>
                  <v-list-item-title>Company</v-list-item-title>
                </v-list-item-content></v-list-item
              >
              <v-list-item v-for="(item, index) in itemsFt2" :key="index" link>
                <v-list-item-content>
                  <v-list-item-subtitle>{{ item.title }}</v-list-item-subtitle>
                </v-list-item-content>
              </v-list-item>
            </v-col>
            <v-col cols="2" sm="2">
              <v-list-item link
                ><v-list-item-content>
                  <v-list-item-title>Customer Service</v-list-item-title>
                </v-list-item-content></v-list-item
              >
              <v-list-item v-for="(item, index) in itemsFt3" :key="index" link>
                <v-list-item-content>
                  <v-list-item-subtitle>{{ item.title }}</v-list-item-subtitle>
                </v-list-item-content>
              </v-list-item>
            </v-col>
            <v-spacer></v-spacer>
            <v-col cols="4" sm="4" class="lg">
              <p><strong>Sign up for our newsistter</strong></p>
              <p class="subtext">
                The latest deals and saving, sent to your inbox weekly.
              </p>
              <div class="textboxfooter">
                <v-text-field></v-text-field
                ><v-btn class="blue lighten-2"> SUBMIT</v-btn>
              </div>
            </v-col>
          </v-row>
        </v-card-title>

        <v-card-text class="py-2 white--text text-center"
          ><strong>Years</strong> {{ new Date().getFullYear() }} —
          <strong>Vuetify</strong>
        </v-card-text>
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
    itemsFt1: [
      { title: "Bage" },
      { title: "Tees" },
      { title: "Object" },
      { title: "Home Goods" },
      { title: "Accessories" },
    ],
    itemsFt2: [
      { title: "Who a are" },
      { title: "Sustainability" },
      { title: "Press" },
      { title: "Careers" },
      { title: "Terms & Conditions" },
      { title: "Privacy" },
    ],
    itemsFt3: [
      { title: "Contact" },
      { title: "Shipping" },
      { title: "Returns" },
      { title: "Warranty" },
      { title: "Secure Payments" },
      { title: "FAQ" },
      { title: "Find a store" },
    ],
  }),
  methods: {
    GotoLogin() {
      console.log("login");
      this.$router.push({ name: "login" });
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

.grid-buttom
  background-color: rgba(220, 220, 220, 1)
  // border: 1px solid rgba(0, 0, 0, 0.8)
  padding: 20px
  font-size: 30px
  column-span: all

// CssFooter
.grid-footer
  background-color: rgba(240, 240, 240, 1)
  // display: grid
  column-count: 2
  max-width: 50rem
  // grid-template-columns: auto auto
  // background-color: #2196F3
  padding: 10px

.grid-footer-item
  background-color: rgba(240, 240, 240, 1)
  // border: 1px solid rgba(0, 0, 0, 0.8)
  padding: 20px
  font-size: 30px
  // text-align: center
  column-span: 1

.grid-footer-button
  background-color: rgba(220, 220, 220, 1)
  // border: 1px solid rgba(0, 0, 0, 0.8)
  padding: 20px
  font-size: 30px
  column-span: all

.subtext
  font-size: 0.75rem
  opacity: 0.7

.textboxfooter
  display: flex
  margin-right: 5rem
  ag
</style>
