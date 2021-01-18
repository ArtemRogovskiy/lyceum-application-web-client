<template>
  <div>
    <v-app-bar color="primary" dark>
<!--      <div class="d-flex align-center">-->
<!--        <v-img alt="MGOL Logo" class="shrink mr-2" contain src="../src/assets/mgol_logo.jpg"-->
<!--               transition="scale-transition" width="40"/>-->
<!--      </div>-->
      <v-app-bar-nav-icon @click.stop="drawer = !drawer"></v-app-bar-nav-icon>

      <v-spacer></v-spacer>

      <v-btn icon>
        <v-icon>mdi-magnify</v-icon>
      </v-btn>

      <v-btn v-if="!isSingIn" @click="loginDialog = !loginDialog" color="indigo">Sign In</v-btn>
      <v-btn v-if="isSingIn">Sign Out</v-btn>
    </v-app-bar>

    <v-navigation-drawer v-model="drawer" absolute bottom temporary>
      <v-list-item to="/">
        <v-list-item-content>
          <v-list-item-title class="title">Application</v-list-item-title>
          <v-list-item-subtitle>subtext</v-list-item-subtitle>
        </v-list-item-content>
      </v-list-item>

      <v-divider></v-divider>

      <v-list nav>
        <v-list-item-group>
          <v-list-item to="/userHome">Личый кабинет</v-list-item>
          <v-list-item to="/news">Новости</v-list-item>
          <v-list-item to="/schedule"> Расписание</v-list-item>
        </v-list-item-group>
      </v-list>
    </v-navigation-drawer>

    <v-row justify="center">
      <v-dialog v-model="loginDialog" persistent max-width="600px">
        <v-card>
          <v-card-title>
            <span class="headline">Вход в личный кабинет</span>
          </v-card-title>
          <v-card-text>
            <v-container>
              <v-row>
                <v-col cols="12">
                  <v-text-field label="Email*" required v-model="email"></v-text-field>
                </v-col>
                <v-col cols="12">
                  <v-text-field label="Пароль*" type="password" required="password" v-model="password"></v-text-field>
                </v-col>
              </v-row>
            </v-container>
          </v-card-text>
          <v-card-actions>
            <v-spacer></v-spacer>
            <v-btn color="blue darken-1" text @click="loginDialog = false">Закрыть</v-btn>
            <v-btn color="blue darken-1" text @click="loginUser">Войти</v-btn>
          </v-card-actions>
        </v-card>
      </v-dialog>
    </v-row>

  </div>
</template>

<script>

// import axios from "axios";

export default {
  name: 'NavigationBar',
  data: () => ({
    drawer: false,
    isSingIn: false,
    loginDialog: false,
    email: '',
    password: ''
  }),

  methods: {
    loginUser: function () {
      console.log("dfdfd" + this.email + " " + this.password)
      this.loginDialog = false;
      // axios.get('http://localhost:8088/users/login/' + '&classLetter=')
      //     .then(response => {
      //       console.log(response.data)
      //       this.posts = response.data
      //     })
      //     .catch(e => {
      //       console.log(e)
      //       this.errors.push(e)
      //     })
    }
  },
};
</script>