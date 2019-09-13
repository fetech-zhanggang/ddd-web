<template>
  <a-card title="Sign Un">
    <nuxt-link slot="extra" :to="{ name: 'users-sign-in' }">
      Or Sign In
    </nuxt-link>
    <a-spin :spinning="spinning">
      <a-form
        class="sign-up-form"
        layout="horizontal"
        :form="form"
        @submit="handleSubmit"
      >
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
            ref="emailInput"
            v-decorator="decorator.email"
            size="large"
            placeholder="Email"
          >
            <a-icon slot="prefix" type="mail" />
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
        <a-form-item align="center">
          <a-divider />
          <a-button block type="primary" size="large" html-type="submit">
            Let's Go!
          </a-button>
        </a-form-item>
      </a-form>
    </a-spin>
  </a-card>
</template>

<script>
export default {
  name: "SignUpForm",
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
        email: [
          "email",
          {
            rules: [{ required: true, message: "Please input your email!" }]
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
          // TODO plugin for $axios to handle error
          this.$axios
            .post("/rest/user/identities", values)
            .then(response => {
              console.log(response)
              this.spinning = false
            })
            .catch(() => {
              this.spinning = false
              this.$message.error(
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
.sign-up-form {
  padding: 0 50px;
}
</style>
