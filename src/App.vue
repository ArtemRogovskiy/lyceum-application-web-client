<template>
<!--  <v-app>-->
<!--    <v-app-bar app color="primary" dark>-->
<!--      <div class="d-flex align-center">-->
<!--        <v-img alt="MGOL Logo" class="shrink mr-2" contain src="../src/assets/mgol_logo.jpg"-->
<!--               transition="scale-transition" width="40"/>-->
<!--      </div>-->

<!--      <v-spacer></v-spacer>-->

<!--      <v-btn href="https://firstlyceum.by/" target="_blank" text>-->
<!--        <span class="mr-2">МГОЛ</span>-->
<!--        <v-icon>mdi-open-in-new</v-icon>-->
<!--      </v-btn>-->
<!--    </v-app-bar>-->

<!--    <v-main>-->
<!--      <HelloWorld/>-->
<!--      <Schedule/>-->
<!--    </v-main>-->
<!--  </v-app>-->
    <v-app>
      <v-app-bar color="primary" dark>
        <v-app-bar-nav-icon @click.stop="drawer = !drawer"></v-app-bar-nav-icon>

        <v-spacer></v-spacer>

        <v-btn icon>
          <v-icon>mdi-magnify</v-icon>
        </v-btn>

        <v-btn icon>
          <v-icon>mdi-filter</v-icon>
        </v-btn>

        <v-btn icon>
          <v-icon>mdi-dots-vertical</v-icon>
        </v-btn>
      </v-app-bar>

      <v-navigation-drawer v-model="drawer" absolute
                           bottom
                           temporary>
        <v-list nav>
          <v-list-item-group v-model="group">
            <v-list-item>
              <v-list-item-title>Foo</v-list-item-title>
            </v-list-item>

            <v-list-item>
              <v-list-item-title>Bar</v-list-item-title>
            </v-list-item>

            <v-list-item>
              <v-list-item-title>Fizz</v-list-item-title>
            </v-list-item>

            <v-list-item>
              <v-list-item-title>Buzz</v-list-item-title>
            </v-list-item>
          </v-list-item-group>
        </v-list>
      </v-navigation-drawer>

      <v-main>
        <HelloWorld/>
        <Schedule/>
      </v-main>

    </v-app>
</template>

<script>
import HelloWorld from './components/HelloWorld';
import Schedule from "./components/Schedule";

export default {
  name: 'App',

  components: {
    HelloWorld,
    Schedule,
  },

  data: () => ({
    schedules: [
      {day: 0, startTime: '9:00', endTime: '9:45', subject: 'math', teacher: 'Иван Иванович', room: 301},
      {day: 0, startTime: '10:00', endTime: '10:45', subject: 'fiz', teacher: 'Иван Иванович Иванов', room: 302},
      {day: 1, startTime: '9:00', endTime: '9:45', subject: 'math', teacher: 'Иван Иванович', room: 303},
      {day: 2, startTime: '9:00', endTime: '9:45', subject: 'math', teacher: 'Иван Иванович', room: 304},
    ],
    drawer: false
  }),
};
</script>
