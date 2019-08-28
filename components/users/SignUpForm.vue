<template>
  <a-card class="login-form" title="Sign In">
    <nuxt-link slot="extra" :to="{ name: 'users-sign-up' }">
      Or Sign Up
    </nuxt-link>
    <a-spin :spinning="spinning">
      <a-form layout="horizontal" :form="form" @submit="handleSubmit">
        <a-form-item>
          <a-input
            ref="usernameInput"
            v-decorator="decorator.username"
            size="large"
            placeholder="Username"
          >
            <a-icon slot="prefix" type="user" />
          </a-input>
        </a-form-item>
        <a-form-item>
          <a-input
            ref="passwordInput"
            v-decorator="decorator.password"
            size="large"
            placeholder="Password"
            type="password"
          >
            <a-icon slot="prefix" type="lock" />
          </a-input>
        </a-form-item>
        <a-form-item>
          <a-checkbox>Remember me</a-checkbox>
          <a class="forgot-password">Forgot password</a>
        </a-form-item>
        <a-form-item>
          <a-button
            type="primary"
            size="large"
            html-type="submit"
            class="login-form-button"
          >
            Log in
          </a-button>
        </a-form-item>
      </a-form>
      <sign-in-by-others />
    </a-spin>
  </a-card>
</template>

<script>
import SignInByOthers from "./SignInByOthers.vue"

export default {
  name: "SignUpForm",
  components: {
    SignInByOthers
  },
  data() {
    return {
      spinning: false,
      decorator: {
        username: [
          "username",
          {
            rules: [{ required: true, message: "Please input your username!" }]
          }
        ],
        password: [
          "password",
          {
            rules: [{ required: true, message: "Please input your password!" }]
          }
        ]
      }
    }
  },
  beforeCreate() {
    this.form = this.$form.createForm(this)
  },
  methods: {
    handleSubmit(e) {
      e.preventDefault()
      this.form.validateFields((err, values) => {
        if (!err) {
          console.log("Received values of form: ", values)
          this.spinning = true
        }
      })
    }
  }
}
</script>

<style scoped>
.login-form {
  height: 520px;
  width: 100%;
  opacity: 1;
}

.forgot-password {
  float: right;
}

.login-form-button {
  width: 100%;
}
</style>
