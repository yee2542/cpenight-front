<template>
  <div
    class="row"
    style="min-height: 100vh; display: grid; grid-template-columns: 50% 50%"
  >
    <div id="right-side">
      <img style="height: 537px" src="@/assets/Logo.png" />
    </div>
    <div style="background: #282667; padding-top: 50px">
      <a href="/" style="text-decoration: none; display: inline" id="backToMain"
        >&lt; Back to Main Page</a
      >
      <div id="left-side" class="column" style="">
        <div>
          <h1 style="text-align: center; margin-top: 90px" class="title">
            LOGIN
          </h1>
          <!-- Input -->
          <div
            class="box"
            style="display: grid; grid-template-columns: 10% 90%"
          >
            <img
              style="height: 43px; margin-top: -5px"
              src="@/assets/icons8-male-user-64.png"
            />
            <input
              v-model="user_input.email"
              class="input"
              type="text"
              placeholder="Email"
            />
          </div>

          <hr
            style="
              margin-top: 20px;
              margin-bottom: 40px;
              height: 2px;
              border: none;
              color: #ffffff;
              background-color: #ffffff;
              font-family: 'CloudLight';
            "
          />

          <div
            class="box"
            style="display: grid; grid-template-columns: 10% 90%"
          >
            <img
              style="height: 37px; margin-top: -5px"
              src="@/assets/icons8-lock-52.png"
            />
            <input
              v-model="user_input.password"
              class="input"
              type="password"
              placeholder="Password"
            />
          </div>

          <hr
            style="
              margin-top: 20px;
              margin-bottom: 20px;
              height: 2px;
              border: none;
              color: #ffffff;
              background-color: #ffffff;
            "
          />

          <p id="forgot">Forgot password ?</p>
          <br />
          <button @click="checkInput()" id="loginButton">LOG IN</button>
          <br />

          <p
            style="
              text-align: center;
              margin-top: 20px;
              margin-bottom: 20px;
              font: normal normal 300 20px/27px Cloud;
              letter-spacing: 1.6px;
              color: #fbdad3;
              opacity: 0.5;
            "
          >
            <span>OR</span>
          </p>

          <img src="@/assets/Google-3.png" />
          <br />
          <img style="margin-top: 15px" src="@/assets/Facebook-3.png" />

          <br />
          <div style="text-align: center; margin-top: 35px">
            <span
              style="
                color: #ffffff;
                letter-spacing: 1.6px;
                font-size: 18px;
                font-family: 'CloudLight';
              "
              >Don't have an account yet ?</span
            >
            <a
              style="
                margin-left: 10px;
                margin-bottom: 240px;
                color: #f28093;
                letter-spacing: 1.6px;
                font-size: 18px;
                font-family: 'CloudLight';
              "
              href="/register"
              >Register</a
            >
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "login_page",
  data() {
    return {
      swap: false,
      user_database: {
        email: "harryphat2000@gmail.com",
        password: "Harryfer2020",
      },
      user_input: {
        email: "",
        password: "",
        hidePassword: true,
      },
    };
  },
  methods: {
    checkInput() {
      if (
        this.user_input.email === this.user_database.email &&
        this.user_input.password === this.user_database.password &&
        !this.showMissmatch
      ) {
        alert("Login Success");
      } else {
        alert("Login Failed");
      }
    },
  },
};
</script>

<style scoped>
#backToMain {
  font-family: "CloudBold";
  font-size: 22px;
  color: #ffffff;
  margin-top: 50px;
  padding-left: 75px;
}

.box {
  margin-top: 15px;
  font-family: "CloudLight";
}

.textDivider {
  width: 100%;
  text-align: center;
  border-bottom: 2px solid #d5d5df;
  line-height: 0.1em;
  margin: 10px 0 20px;
}

input[type="text"] {
  color: white;
  font-size: 26px;
  font-family: "CloudLight";
}

input[type="password"] {
  color: white;
  font-size: 26px;
  font-family: "CloudLight";
}

#loginButton {
  color: #ffffff;
  background-color: #f28093;
  border: none;
  width: 100%;
  padding-top: 14px;
  padding-bottom: 14px;
  font-size: 30px;
  letter-spacing: 3px;
  font-family: "CloudBold";
}

input[type="text"]:focus {
  border: none;
  background-color: none;
  outline: 0;
}

input[type="password"]:focus {
  border: none;
  background-color: none;
  outline: 0;
}

::placeholder {
  color: #bbbde4;
  font-size: 26px;
  font-family: "CloudLight";
}

.input {
  margin-left: 10px;
  padding-left: 10px;
  background: transparent;
  border: none;
}
body,
html {
  padding: 0;
  margin: 0;
}

#forgot {
  text-align: right;
  font-size: 18px;
  font-family: "CloudLight";
  color: white;
  margin-bottom: 0px;
  opacity: 0.7;
}
.title {
  font-size: 112px;
  font-family: "CloudBold";
  letter-spacing: 11.6px;
  color: #ffffff;
  opacity: 1;
  margin-bottom: 0px;
  margin-top: 0px;
  z-index: 2;
}

#left-side {
  background-color: #282667;
  display: flex;
  justify-content: center;
  align-items: top;
}

#right-side {
  background-color: #312e71;
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>