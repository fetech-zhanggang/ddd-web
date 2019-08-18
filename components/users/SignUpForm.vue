<template>
  <a-card class="login-form" title="Sign In">
    <nuxt-link :to="{name:'users-sign-up'}" slot="extra">Sign Up</nuxt-link>
    <a-form layout="horizontal" :form="form" @submit="handleSubmit">
      <a-form-item>
        <a-input v-decorator="decorator.username" size="large" placeholder="Username" ref="usernameInput">
          <a-icon slot="prefix" type="user"/>
        </a-input>
      </a-form-item>
      <a-form-item>
        <a-input v-decorator="decorator.password" size="large" placeholder="Password" type="password"
                 ref="passwordInput">
          <a-icon slot="prefix" type="lock"/>
        </a-input>
      </a-form-item>
      <a-form-item>
        <a-checkbox>Remember me</a-checkbox>
        <a class="forgot-password">Forgot password</a>
      </a-form-item>
      <a-form-item>
        <a-button type="primary" size="large" html-type="submit" class="login-form-button">
          Log in
        </a-button>
      </a-form-item>
    </a-form>
    <Sign-In-By-Others/>
  </a-card>
</template>

<script>
    import SignInByOthers from '~/components/users/SignInByOthers.vue'

    export default {
        name: "SignUpForm",
        components: {
            SignInByOthers
        },
        data() {
            return {
                decorator: {
                    username: [
                        'username',
                        {rules: [{required: true, message: 'Please input your username!'}]}
                    ],
                    password: [
                        'password',
                        {rules: [{required: true, message: 'Please input your password!'}]}
                    ]
                }
            }
        },
        beforeCreate() {
            this.form = this.$form.createForm(this);
        },
        methods: {
            handleSubmit(e) {
                e.preventDefault();
                this.form.validateFields((err, values) => {
                    if (!err) {
                        console.log('Received values of form: ', values);
                    }
                });
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
