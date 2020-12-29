<template>
  <v-container>
    <div v-if="showSelectNeeded">
      <v-alert icon="mdi-school" prominent text type="info">
        Выберите класс для просмотра расписания
      </v-alert>
    </div>
    <div v-if="showWarning">
      <v-alert text prominent type="error">
        Расписание не найдено
      </v-alert>
    </div>
    <v-col>
      <v-select
          :items="classes"
          :menu-props="{ top: true, offsetY: true }"
          label="Номер класс"
          v-model="classNumber"
      ></v-select>
    </v-col>
    <v-col>
      <v-select
          :items="letters"
          :menu-props="{ top: true, offsetY: true }"
          label="Буква"
          v-model="classLetter"
      ></v-select>
    </v-col>
    <v-col>
      <v-btn @click="loadSchedule">Применить</v-btn>
    </v-col>
    <div v-if="showSchedule">
      <v-col v-for="day in days" :key="day.number" cols="12">
        <ScheduleItem
            v-bind:schedule="posts.filter(item => item.day === day.number)"
            v-bind:dayOfWeek="day"
        />
      </v-col>
    </div>
  </v-container>
</template>

<script>
import ScheduleItem from "@/components/ScheduleItem";
import axios from 'axios';

export default {
  name: "Schedule",
  components: {ScheduleItem},
  data: () => ({
    posts: [],
    errors: [],
    days: [
      {name: 'Понедельник', number: 0},
      {name: 'Вторник', number: 1},
      {name: 'Среда', number: 2},
      {name: 'Четверг', number: 3},
      {name: 'Пятница', number: 4},
      {name: 'Суббота', number: 5}],
    classes: [9, 10, 11],
    letters: ["А", "Б", "В", "Г", "Д", "Е", "Ж", "З"],
    classNumber: '11',
    classLetter: 'а',
    showSchedule: false,
    showWarning: false,
    showSelectNeeded: true
  }),

  methods: {
    loadSchedule: function () {
      axios.get('http://localhost:8088/schedules/class?classNumber=' + this.classNumber + '&classLetter=' + this.classLetter)
          .then(response => {
            console.log(response.data)
            this.posts = response.data
            if (this.posts.length === 0) {
              this.showWarning = true;
              this.showSelectNeeded = false;
              this.showSchedule = false;
            } else {
              this.showWarning = false;
              this.showSchedule = true;
              this.showSelectNeeded = false;
            }

          })
          .catch(e => {
            console.log(e)
            this.errors.push(e)
            this.showWarning = true;
          })
    }
  },

  watch: {
    loader() {
      console.log('in creted() method')
    }
  },

  created() {
    console.log('in creted() method')
    axios.get(`http://localhost:8088/schedules/class?classNumber=10&classLetter=а`)
        .then(response => {
          console.log(response.data)
          this.posts = response.data
        })
        .catch(e => {
          console.log(e)
          this.errors.push(e)
        })
  }
}
</script>