<template>
  <section class="section has-background-primary">
    <div class="container has-text-centered">
      <h1 class="title is-spaced has-text-white">Dashboard</h1>
      <h2 class="subtitle has-text-white">
        Upcoming events in your area
      </h2>
      <hr style="width:50%;margin:auto;" />
      <template v-if="!isLoading">
        <EventCard v-for="event in events" :key="event.id" :event="event" />
      </template>
    </div>
  </section>
</template>

<script>
import axios from 'axios'
import EventCard from '@/components/EventCard'

export default {
  components: { EventCard },
  data() {
    return {
      isLoading: true,
      events: []
    }
  },
  created() {
    axios.get('//localhost:3000/dashboard').then(({ data }) => {
      this.events = data.events.events
      this.isLoading = false
    })
  }
}
</script>
