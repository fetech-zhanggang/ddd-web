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
            v-decorator="decorator.usernameOrEmail"
            size="large"
            placeholder="Username/Email"
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
  name: "SignInForm",
  components: {
    SignInByOthers
  },
  data() {
    return {
      spinning: false,
      decorator: {
        usernameOrEmail: [
          "usernameOrEmail",
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
          this.spinning = true
          this.$axios
            .post("/rest/user/identities/authentication", values)
            .then(response => {
              console.log(response)
              this.spinning = false
            })
            .catch(() => {
              self.spinning = false
              self.$message.error(
                "Oops! Server was tired out, please try later."
              )
            })
          console.log("Received values of form: ", values)
        }
      })
    }
  }
}
</script>

<style scoped>
.login-form {
  height: 435px;
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
