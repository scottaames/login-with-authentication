<template>
  <div class="hero is-fullheight-with-navbar is-primary is-bold">
    <div class="hero-body">
      <div class="container has-text-centered">
        <div class="columns is-centered is-mobile">
          <div class="column is-4-desktop is-6-tablet is-10-mobile">
            <div class="box">
              <p class="title is-4 has-text-dark">
                Login
              </p>
              <form @submit.prevent="login" style="margin: 0 2em;">
                <b-field label="Email" label-position="inside">
                  <b-input type="email" v-model="email"></b-input>
                </b-field>
                <b-field label="Password" label-position="inside">
                  <b-input type="password" v-model="password"></b-input>
                </b-field>
                <b-field grouped position="is-centered">
                  <p class="control">
                    <button
                      type="submit"
                      class="button is-link"
                      style="margin-bottom: 8px;"
                    >
                      Submit
                    </button>
                  </p>
                </b-field>
                <span>{{ error }}</span>
              </form>
              <router-link to="/register">
                Don't have an account? Register.
              </router-link>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      email: '',
      password: '',
      error: null
    }
  },
  methods: {
    login() {
      this.$store
        .dispatch('login', {
          email: this.email,
          password: this.password
        })
        .then(() => {
          this.$router.push({ name: 'dashboard' })
        })
        .catch(err => {
          this.error = err.response.data.error
        })
    }
  }
}
</script>

<style lang="scss" scoped></style>
