<script setup>
import EventCard from '@/components/EventCard.vue'
import { onMounted, ref } from 'vue';
import axios from 'axios'

const events = ref(null)

onMounted(() => {
  axios
  .get('http://my-json-server.typicode.com/latifcodess/294-VueComposition/events')
  .then((response) => {
    events.value = response.data
  })
  .catch((error) => {
    console.log(error)
  })
})
</script>

<template>
  <h1>Events for good</h1>
  <div class="events">
    <EventCard v-for="event in events" :key="event.id" :event="event" />
  </div>
</template>

<style scoped>
.events{
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>