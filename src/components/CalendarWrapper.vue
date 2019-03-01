<template>
    <div class="calendar-wrapper">
        <Calendar 
            :month="month" 
            :day="day" 
            :startOfMonth="monthDayStart" 
            :endOfMonth="monthDayEnd"
            :numberOfDays="numberOfDays"/>
    </div>
</template>

<script>
import moment from "moment";
import Calendar from "./Calendar.vue";
export default {
  name: "CalendarWrapper",
  components: { Calendar },
  computed: {
    month() {
      return moment().format("MMMM");
    },
    day() {
      return moment().format("D");
    }
  },
  data() {
    return {
      monthDayStart: moment()
        .startOf("month")
        .format("dddd"),
      monthDayEnd: moment()
        .endOf("month")
        .format("dddd"),
      numberOfDays: moment().daysInMonth()
    };
  }
};
</script>

<style>
.calendar-wrapper {
  height: 100%;
}
.calendar-days {
  display: flex;
  flex-direction: column;
}
.week {
  flex: 1;
  display: flex;
  flex-direction: row;
  flex-wrap: none;
}
.day {
  border: 1px solid grey;
  height: 100px;
  padding: 1rem;
  flex: 1;
  font-weight: bold;
}
.name {
  border: none;
  height: unset;
}
</style>

