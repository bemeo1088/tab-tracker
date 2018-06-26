<template>
  <v-toolbar fixed class="cyan" dark>
    <v-toolbar-title class="mr-4">
      <span
        class="home"
        @click="navigateTo({name: 'root'})">
        Tab Tracker
      </span>
    </v-toolbar-title>
    <v-toolbar-items>
      <v-btn
        flat
        dark
        @click="navigateTo({name: 'songs'})">
        Browse
      </v-btn>
    </v-toolbar-items>

    <v-spacer></v-spacer>

    <v-toolbar-items>
      <v-btn
        v-if="!$store.state.isUserLoggedIn"
        flat
        dark
        @click="navigateTo({name: 'register'})">
        <!-- <router-link to="register">Sign Up</router-link> -->
        Sign Up
      </v-btn>
    </v-toolbar-items>
    <v-toolbar-items>
      <v-btn
        v-if="!$store.state.isUserLoggedIn"
        flat
        dark
        @click="navigateTo({name: 'login'})">
        <!-- <router-link to="register">Sign Up</router-link> -->
        Log In
      </v-btn>

      <v-btn
        flat
        dark
        @click="logout()">
        <!-- <router-link to="register">Sign Up</router-link> -->
        Log Out
      </v-btn>
    </v-toolbar-items>
  </v-toolbar>
</template>

<script>
export default {
  methods: {
    navigateTo (route) {
      this.$router.push(route)
    },
    logout () {
      this.$store.dispatch('setToken', null)
      this.$store.dispatch('setUser', null)
      this.$router.push({
        name: 'root'
      })
    }
  }
}
</script>

<style scoped>
.home {
  cursor: pointer;
}

.home:hover {
  color: pink;
}
</style>
