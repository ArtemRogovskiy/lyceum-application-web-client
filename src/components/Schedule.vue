<template>
  <v-container>
    <v-col v-for="day in days" :key="day.number" cols="12">
      <ScheduleItem
          v-bind:schedule="schedules.filter(item => item.day === day.number)"
          v-bind:dayOfWeek="day"
      />
    </v-col>
  </v-container>
</template>

<script>
import ScheduleItem from "@/components/ScheduleItem";

export default {
  name: "Schedule",
  components: {ScheduleItem},
  props: ['schedules'],
  data: () => ({
    days: [
      {name: 'Понедельник', number: 0},
      {name: 'Вторник', number: 1},
      {name: 'Среда', number: 2},
      {name: 'Четверг', number: 3},
      {name: 'Пятница', number: 4},
      {name: 'Суббота', number: 5}],
  }),
}
</script>