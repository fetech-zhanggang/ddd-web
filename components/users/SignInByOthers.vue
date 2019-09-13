<template>
  <div>
    <a-divider>Or Sign In With</a-divider>
    <a-row class="sign-in-button">
      <a-col align="center" :span="24">
        <a-button>FETECH Community</a-button>
      </a-col>
    </a-row>
  </div>
</template>

<script>
export default {
  name: "SignInByOthers"
}
</script>

<style scoped>
.sign-in-button button {
  margin-bottom: 10px;
  width: 85%;
}
</style>
