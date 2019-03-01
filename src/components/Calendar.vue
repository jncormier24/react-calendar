<template>
    <div class="calendar-wrapper">
        <h1>{{ month }} - {{ day }}</h1>
        <div class="day-names week">
            <div class="day name" v-for="(name, key) in dayNames" :key="key">
                {{ name }}
            </div>
        </div>
        <div class="calendar-days">
            <Day v-for="day in numberOfDays" :key="day" :number="day" name="day" />
        </div>
    </div>
</template>

<script>
import moment from "moment";
import Day from "./Day.vue";
export default {
  name: "Calendar",
  components: { Day },
  props: ["month", "day", "startOfMonth", "endOfMonth", "numberOfDays"],
  data() {
    return {
      dayNames: [
        "Sunday",
        "Monday",
        "Tuesday",
        "Wednesday",
        "Thursday",
        "Friday",
        "Saturday"
      ],
      listOfDays: []
    };
  },
  created() {
    this.createListOfDays();
  },
  methods: {
    createListOfDays() {
      let index = this.dayNames.indexOf(this.startOfMonth);
      for (let i = 0; i < this.numberOfDays; i++) {
        this.listOfDays[i] = this.dayNames[index];
        index < 6 ? index++ : (index = 0);
      }
    }
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

