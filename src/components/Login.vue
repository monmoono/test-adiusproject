<template>
  <v-container class="fill-height" fluid>
    <v-row align="center" justify="center" dense>
      <v-col cols="12" sm="8" md="4" lg="4">
        <v-card elevation="0">
          <v-img
            src="@/assets/logo.png"
            alt="Fedorae Education Log"
            contain
            height="80"
          ></v-img>
          <div class="text-left">
            <h1 class="mb-2">Sign in to your account</h1>
            <h5>Or <a>start your 14-day free trial</a></h5>
          </div>
          <v-divider></v-divider>
          <div style="padding-top: 20px">
            <h4>Sign in with</h4>
            <v-btn
              class="btnSignin"
              color="grey lighten-2"
              href="https://www.facebook.com/login.php/"
              target="_blank"
            >
              <v-icon>mdi-facebook</v-icon>
            </v-btn>
            <v-btn
              class="btnSignin"
              color="grey lighten-2"
              href="https://twitter.com/login/"
              target="_blank"
            >
              <v-icon>mdi-twitter</v-icon>
            </v-btn>
            <v-btn
              class="btnSignin"
              color="grey lighten-2"
              href="https://www.facebook.com/login.php/"
              target="_blank"
            >
              <v-icon>mdi-github</v-icon>
            </v-btn>
          </div>
          <h5 class="h5-line">Or continue with</h5>
          <v-card-text>
            <v-form>
              <v-text-field
                v-model="email"
                label="Enter your email"
                name="email"
                prepend-inner-icon="mdi-email"
                type="email"
                class="rounded-0"
                outlined
              ></v-text-field>
              <v-text-field
                v-model="password"
                label="Enter your password"
                name="password"
                prepend-inner-icon="mdi-lock"
                type="password"
                class="rounded-0"
                outlined
              ></v-text-field>
              <v-card-actions>
                <v-checkbox
                  color="#000000"
                  v-model="ChkRemember"
                  label="Remember me"
                ></v-checkbox>
                <v-spacer></v-spacer>
                <a helf="">Forgot your password?</a>
              </v-card-actions>
              <v-btn
                class="rounded-0"
                color="blue lighten-2"
                x-large
                block
                dark
                @click="Login"
                >Login</v-btn
              >
            </v-form>
          </v-card-text>
        </v-card>
      </v-col>
      <v-col cols="12" sm="8" md="4" lg="4">
        <v-img
          src="@/assets/wallpaper.jpg"
          aspect-ratio="1"
          max-height="1000"
          height="650"
          max-width="600"
        ></v-img>
      </v-col>

      <!-- toast -->
      <v-snackbar
        v-model="snackbar"
        :timeout="1000"
        :value="true"
        absolute
        top
        color="error"
      >
        <v-icon dark large> mdi-cancel </v-icon>
        {{ "Email or password is wrong." }}

        <template v-slot:action="{ attrs }">
          <v-btn color="pink" text v-bind="attrs" @click="snackbar = false">
            X
          </v-btn>
        </template>
      </v-snackbar>
    </v-row>
  </v-container>
</template>

<script>
import axios from "axios";
export default {
  name: "app-login",
  data: () => ({
    email: "",
    password: "",
    ChkRemember: "",
    snackbar: false,
  }),
  methods: {
    Login() {
      // Test Login
      //  body:{
      //   email: "eve.holt@reqres.in",
      //   password: "cityslicka"
      //}
      axios
        .post("https://reqres.in/api/login", {
          email: this.email,
          password: this.password,
        })
        .then((response) => {
          console.log("success", response);
          //check remember me == true setItemlocalStorage
          if (this.ChkRemember) {
            console.log(this.ChkRemember);
            const vals = JSON.stringify({
              email: this.email,
              password: this.password,
              ChkRemember: this.ChkRemember,
            });
            localStorage.setItem("localVals", vals);
          } else {
            localStorage.removeItem("localVals");
          }
          this.$router.push({ name: "dataEmployeePage" });
        })
        .catch((err) => {
          this.snackbar = true;
          console.log("error", err);
        });
    },
  },
  mounted() {
    if (localStorage.getItem("localVals")) {
      try {
        console.log(JSON.parse(localStorage.getItem("localVals")));
        var jsonLocal = JSON.parse(localStorage.getItem("localVals"));
        this.email = jsonLocal.email;
        this.password = jsonLocal.password;
        this.ChkRemember = jsonLocal.ChkRemember;
      } catch (e) {
        localStorage.removeItem("localVals");
      }
    }
  },
};
</script>

<style lang="sass" scoped>
.btnSignin
  width: 9rem
  margin: 0.5rem

.h5-line
  position: relative
  z-index: 1
  overflow: hidden
  text-align: center

.h5-line:before, .h5-line:after
  position: absolute
  top: 51%
  overflow: hidden
  width: 50%
  height: 1px
  content: '\a0'
  background-color: #E0E0E0

.h5-line:before
  margin-left: -50%
  text-align: right
</style>
