<template>
  <div>
    <h1>Event Listing</h1>
    <EventCard v-for="event in events" :key="event.id" :event="event" />
  </div>
</template>

<script>
import EventCard from '@/components/EventCard'
import EventService from '@/services/EventService'

export default {
  components: {
    EventCard
  },

  data () {
    return {
      events: []
    }
  },

  created () {
    EventService.getEvents()
      .then(res => {
        this.events = res.data
      })
      .catch(error => {
        console.log(error)
      })
  }
}
</script>
