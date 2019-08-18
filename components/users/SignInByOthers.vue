<template>
  <div>
    <a-divider>Or Sign In With</a-divider>
    <a-row class="sign-in-button">
      <a-col align="center" :span="12">
        <a-button>Google</a-button>
      </a-col>
      <a-col align="center" :span="12">
        <a-button>Microsoft</a-button>
      </a-col>
      <a-col align="center" :span="12">
        <a-button>WeChat</a-button>
      </a-col>
      <a-col align="center" :span="12">
        <a-button>Alipay</a-button>
      </a-col>
      <a-col align="center" :span="12">
        <a-button>Facebook</a-button>
      </a-col>
      <a-col align="center" :span="12">
        <a-button>GitHub</a-button>
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
