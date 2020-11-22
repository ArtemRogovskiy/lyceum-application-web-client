<template>
  <v-app>
    <v-app-bar app color="primary" dark>
      <div class="d-flex align-center">
        <v-img alt="MGOL Logo" class="shrink mr-2" contain src="../src/assets/mgol_logo.jpg"
               transition="scale-transition" width="40"/>
      </div>

      <v-spacer></v-spacer>

      <v-btn href="https://firstlyceum.by/" target="_blank" text>
        <span class="mr-2">МГОЛ</span>
        <v-icon>mdi-open-in-new</v-icon>
      </v-btn>
    </v-app-bar>

    <v-main>
      <HelloWorld/>
      <Schedule
          v-bind:schedules="schedules"/>
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
    ]
  }),
};
</script>
