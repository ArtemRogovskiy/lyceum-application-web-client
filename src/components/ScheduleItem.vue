<template>
  <v-card>
    <v-subheader>{{ dayOfWeek.name }}</v-subheader>
    <v-list two-line>
      <template v-for="scheduleItem in schedule">
        <v-list-item :key="scheduleItem.startTime">
          <v-list-item-content>
            <v-list-item-title>{{ scheduleItem.startTime.substr(0, scheduleItem.startTime.length - 3) }}
              - {{ scheduleItem.endTime.substr(0, scheduleItem.endTime.length - 3) }} {{
                scheduleItem.subject
              }}
            </v-list-item-title>
            <v-list-item-subtitle>
              Кабинет: {{ scheduleItem.room }}, учитель: {{ scheduleItem.teacherSurname }} {{
                scheduleItem.teacherName
              }} {{ scheduleItem.middleName }}
            </v-list-item-subtitle>
          </v-list-item-content>
        </v-list-item>
      </template>
    </v-list>
  </v-card>
</template>

<script>
export default {
  name: "ScheduleItem",

  props: {
    dayOfWeek: {
      type: Object,
      required: true
    },
    schedule: {
      required: true
    }
  }
}
</script>
