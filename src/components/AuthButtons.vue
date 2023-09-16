<template>
  <ul class="navbar-nav ms-auto">
    <!-- Unauthenticated state -->
    <li class="nav-item" v-if="!isAuthenticated">
      <a href="#" class="nav-link" @click="login">Login</a>
    </li>
    <li class="nav-item" v-if="!isAuthenticated">
      <button class="btn btn-primary navbar-btn" @click="signup">Sign up!</button>
    </li>
    <!-- Authenticated state -->
    <li class="nav-item" v-if="isAuthenticated">
      <a href="#" class="nav-link" @click="logout">Logout</a>
    </li>
    <li class="nav-item" v-if="isAuthenticated">
      <button class="btn btn-primary navbar-btn">My Account</button>
    </li>
  </ul>
</template>

<script>
export default {
  name: "AuthButtons",
  data() {
    return {
      isAuthenticated: false // you'll need to link this to your authentication logic
    };
  },
  methods: {
    login() {
      // login logic
    },
    signup() {
      // signup logic
    },
    logout() {
      // logout logic
    }
  }
}
</script>

<style scoped>

</style>