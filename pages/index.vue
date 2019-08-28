<template>
  <div>
    <nuxt-link :to="{ name: 'users-sign-in' }">
      Sign In
    </nuxt-link>
  </div>
</template>

<script>
export default {
  head() {
    return {
      title: "DuDaDu"
    }
  }
}
</script>

<style></style>
