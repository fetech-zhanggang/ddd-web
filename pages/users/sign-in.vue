<template>
  <div id="container">
    <a-row class="login-top">
      <a-col class="login-right" :span="14">
        <a-row>
          <a-col align="center" :span="24">
            <img src="~assets/ddd.png" alt="" />
          </a-col>
        </a-row>
      </a-col>
      <a-col :span="10">
        <a-row>
          <a-col align="center" class="login-header" :span="14">
            <p>DuDaDu</p>
          </a-col>
        </a-row>
        <a-row>
          <a-col :span="14">
            <sign-up-form />
          </a-col>
        </a-row>
      </a-col>
    </a-row>
    <a-row class="login-bottom">
      <a-col class="login-bottom-content" :span="24">
        Learn more about DuDaDu.
      </a-col>
    </a-row>
  </div>
</template>

<script>
import SignUpForm from "~/components/users/SignUpForm.vue"

export default {
  components: {
    SignUpForm
  }
}
</script>

<style scoped>
.login-top {
  height: 90vh;
}

.login-bottom {
  height: 10vh;
}

.login-bottom .login-bottom-content {
  color: white;
  font-size: 18px;
  text-align: center;
  position: absolute;
  bottom: 0;
  margin-bottom: 5px;
}

#container {
  background-image: url("~assets/index.png");
  background-repeat: no-repeat;
  background-size: cover;
  height: 100vh;
}

.login-right {
  color: white;
}

.login-right img {
  margin-top: 170px;
  height: 300px;
  width: 300px;
}

.login-right h1 {
  color: white;
}

.login-header {
  padding-top: 20px;
  height: 110px;
}

.login-header p {
  color: white;
  font-size: 60px;
  font-family: "phosphate", serif;
}
</style>
