<template>
  <div v-if="event">
    <h1>{{event.title}}</h1>
    <p>{{event.time}} on {{event.date}} @ {{event.location}}</p>
    <p>{{event.description}}</p>
  </div>
</template>

<script setup lang="ts">
import {ref} from 'vue'
import type { Event } from '@/types/Event';
import EventService from '@/services/EventService';
const event=ref({} as Event)
const props=defineProps<{
  id:number
}>()
EventService.getEvent(props.id)
.then((response)=>event.value=response.data)
.catch((error=>console.log(error)))
</script>

<style scoped>

</style>