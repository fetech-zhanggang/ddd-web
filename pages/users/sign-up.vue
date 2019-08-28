<template>
  <div>
    <p>Sign Up</p>
    <nuxt-link :to="{ name: 'users-sign-in' }">
      Sign In
    </nuxt-link>
  </div>
</template>

<script>
export default {
  name: "SignUp"
}
</script>

<style scoped></style>
