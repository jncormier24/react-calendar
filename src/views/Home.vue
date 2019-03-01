<template>
  <div class="home">
    <CalendarWrapper />
  </div>
</template>

<script>
// @ is an alias to /src
import CalendarWrapper from "@/components/CalendarWrapper.vue";

export default {
  name: "home",
  components: {
    CalendarWrapper
  }
};
</script>
