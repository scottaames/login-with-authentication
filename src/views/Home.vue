<template>
  <div class="hero is-fullheight-with-navbar is-primary is-bold">
    <div class="hero-body page">
      <div class="container has-text-centered">
        <h1 class="title is-spaced has-text-weight-bold">
          Welcome to Login App w/ Authentication!
        </h1>
        <h2 class="subtitle" v-if="!loggedIn">
          To use this app you'll need to
          <router-link class="has-text-link" to="/login">
            Login
          </router-link>
          or
          <router-link class="has-text-link" to="/register">
            Register
          </router-link>
        </h2>
      </div>
    </div>
  </div>
</template>

<script>
import { authComputed } from '../store/helpers.js'
export default {
  computed: {
    ...authComputed
  }
}
</script>
