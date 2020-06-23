<template>
  <div class="hero is-fullheight-with-navbar is-primary is-bold">
    <div class="hero-body">
      <div class="container has-text-centered">
        <div class="columns is-centered is-mobile">
          <div class="column is-4-desktop is-6-tablet is-10-mobile">
            <div class="box">
              <p class="title is-4 has-text-dark">
                Register
              </p>
              <form @submit.prevent="register" style="margin: 0 2em;">
                <b-field label="Name" label-position="inside">
                  <b-input type="text" v-model="name"></b-input>
                </b-field>
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
                <ul>
                  <li v-for="(error, index) in errors" :key="index">
                    {{ error }}
                  </li>
                </ul>
              </form>
              <router-link to="/login">
                Already have an account? Login.
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
      name: '',
      email: '',
      password: '',
      errors: []
    }
  },
  methods: {
    register() {
      this.$store
        .dispatch('register', {
          name: this.name,
          email: this.email,
          password: this.password
        })
        .then(() => {
          this.$router.push({ name: 'dashboard' })
        })
        .catch(err => {
          this.errors = err.response.data.errors
        })
    }
  }
}
</script>

<style lang="scss" scoped></style>
