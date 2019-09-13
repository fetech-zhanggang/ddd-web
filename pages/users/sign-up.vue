<template>
  <div class="index-background height-100">
    <a-row>
      <a-col align="center" class="ddd-header" :span="24">
        <p>DuDaDu</p>
      </a-col>
    </a-row>
    <a-row>
      <a-col align="center" :span="7" />
      <a-col :span="10">
        <sign-up-form />
      </a-col>
      <a-col align="center" :span="7" />
    </a-row>
  </div>
</template>

<script>
import SignUpForm from "../../components/users/SignUpForm"

export default {
  name: "SignUp",
  components: { SignUpForm }
}
</script>

<style scoped>
.ddd-header {
  padding-top: 20px;
  height: 110px;
}

.ddd-header p {
  color: white;
  font-size: 60px;
  font-family: "phosphate", serif;
}
</style>
