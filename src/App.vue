<template>
  <div>
    <p>Spaces lef: {{ spacesLeft }} out of {{ capacity }}</p>
    <p>Capacity: {{ capacity }}</p>
    <button @click="increaseCapacity">Increate capacity</button>
    <ul>
      <li v-for="(name, index) in attending" :key="index">{{ name }}</li>
    </ul>
  </div>
</template>

<script>
import { computed, reactive, toRefs } from "vue";

export default {
  setup() {
    const event = reactive({
      capacity: 10,
      attending: ["John", "Jane", "Bob"],
      spacesLeft: computed(() => event.capacity - event.attending.length),
    });

    function increaseCapacity() {
      event.capacity++;
    }

    return { ...toRefs(event), increaseCapacity };
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
