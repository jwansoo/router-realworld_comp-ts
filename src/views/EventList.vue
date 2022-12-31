<template>
  <div class="events">
    <h1>Event For Good</h1>
    <EventCard 
    v-for="event in events"
    :key="event.id"
    :event="event"
    />
  </div>
</template>

<script setup lang="ts">
import EventCard from '@/components/EventCard.vue';
import EventService from '../services/EventService'
import type { Event } from '@/types/Event';
import {ref} from 'vue'
const events=ref([] as Event[]) 
EventService.getEvents()
.then((response)=>{
  events.value=response.data
})
.catch((error)=>console.log(error)
)
</script>

<style scoped>
.events {
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>