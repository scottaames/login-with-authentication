<template>
  <div class="card">
    <header class="card-header">
      <p class="card-header-title is-centered">
        {{ event.title }}
      </p>
    </header>
    <div class="card-content">
      <span>@{{ event.time }} on {{ event.date }}</span>
    </div>
    <footer class="card-footer">
      <a href="#" class="card-footer-item">RSVP</a>
      <a href="#" class="card-footer-item">Details</a>
      <a href="#" class="card-footer-item">Save</a>
    </footer>
  </div>
</template>

<script>
export default {
  name: 'EventCard',
  props: {
    event: {
      type: Object,
      default: () => {
        return {}
      }
    }
  }
}
</script>

<style scoped>
.card {
  max-width: 20em;
  margin: 1em auto 1em auto;
  transition: all 0.2s linear;
}
.card:hover {
  transform: scale(1.01);
  box-shadow: 0 3px 12px 0 rgba(0, 0, 0, 0.2), 0 1px 15px 0 rgba(0, 0, 0, 0.19);
}
</style>
