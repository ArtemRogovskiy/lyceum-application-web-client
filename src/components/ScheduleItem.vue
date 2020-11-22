<template>
  <v-card>
    <v-subheader>{{ dayOfWeek.name }}</v-subheader>
    <v-list two-line>
      <template v-for="scheduleItem in schedule">
        <v-list-item :key="scheduleItem.startTime">
          <v-list-item-content>
            <v-list-item-title>{{ scheduleItem.startTime }} - {{ scheduleItem.endTime }} {{
                scheduleItem.subject
              }}
            </v-list-item-title>
            <v-list-item-subtitle>
              Кабинет: {{ scheduleItem.room }}, учитель: {{ scheduleItem.teacher }}
            </v-list-item-subtitle>
          </v-list-item-content>
        </v-list-item>
      </template>
    </v-list>
  </v-card>
</template>

<script>
export default {
  props: {
    dayOfWeek: {
      type: Object,
      required: true
    },
    schedule: {
      type: Object,
      required: true
    }
  },
  name: "ScheduleItem"
}
</script>
