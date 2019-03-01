<template>
    <div class="day">
        <span class="number">{{ number }}</span>
        
    </div>
</template>

<script>
export default {
  name: "Day",
  props: ["name", "number"]
};
</script>
