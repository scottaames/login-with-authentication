<template>
  <b-navbar type="is-white">
    <template slot="brand">
      <b-navbar-item tag="router-link" :to="{ path: '/' }">
        <img
          src="https://mockit.gg/wp-content/uploads/2017/03/mockit-icon.png"
        />
      </b-navbar-item>
    </template>
    <template slot="start">
      <b-navbar-item href="/">
        Home
      </b-navbar-item>
      <b-navbar-item v-if="loggedIn" href="/dashboard">
        Dashboard
      </b-navbar-item>
    </template>

    <template slot="end">
      <div class="buttons" v-if="!loggedIn">
        <b-navbar-item tag="button" class="button is-link" href="/register">
          Register
        </b-navbar-item>

        <b-navbar-item class="button" href="/login">
          Login
        </b-navbar-item>
      </div>
      <b-navbar-item v-else class="button" @click="logout">
        Logout
      </b-navbar-item>
    </template>
  </b-navbar>
</template>

<script>
import { authComputed } from '../store/helpers.js'
export default {
  computed: {
    ...authComputed
  },
  methods: {
    logout() {
      this.$store.dispatch('logout')
    }
  }
}
</script>

<style lang="scss" scoped></style>
