<template>
  <div id="register2">
    <div
      class="row"
      style="min-height: 100vh; display: grid; grid-template-columns: 37% 63%"
    >
      <div id="left-side">
        <img style="height: 537px" src="@/assets/Logo.png" />
      </div>
      <div style="background: #282667; padding-top: 50px">
        <a
          href="/"
          style="text-decoration: none; display: inline"
          id="backToMain"
        >
          &lt; Back to Main Page
        </a>
        <div id="right-side" class="column">
          <div>
            <h1 style="margin-top: 30px" class="title">REGISTER</h1>
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
                @input="updateValue"
                class="input"
                type="password"
                placeholder="Password"
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
              "
            />

            <div
              class="box"
              style="display: grid; grid-template-columns: 10% 90%"
            >
              <img
                style="height: 45px; margin-top: -5px"
                src="@/assets/Confirm Pass.png"
              />
              <input
                v-model="user_input.confirmPassword"
                class="input"
                type="password"
                placeholder="Confirm Password"
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

            <div class="validatePassword">
              <p :class="changeColor1()">Must have more than 8 characters</p>
              <p :class="changeColor2()">Must have at least 1 uppercase</p>
              <p :class="changeColor3()">Must have at least 1 number</p>
              <p :class="changeColor4()">
                Must have at least 1 special characters
              </p>
            </div>
            <!-- <br> -->
            <button
              @click="checkRegister()"
              id="loginButton"
              style="margin-bottom: 20px; background-color: #f28093"
            >
              REGISTER
            </button>
            <br />

            <br />

            <div style="text-align: center; margin-top: 5px">
              <span
                style="
                  color: #ffffff;
                  letter-spacing: 1.6px;
                  font-size: 18px;
                  font-family: 'CloudBold';
                "
                >Already have an account ?</span
              >
              <a
                style="
                  margin-left: 10px;
                  color: #f28093;
                  letter-spacing: 1.6px;
                  font-size: 18px;
                  font-family: 'CloudBold';
                "
                href="/login"
                >Login</a
              >
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "register2",
  computed: {
    showMissmatch: function () {
      if (
        this.user_input.password !== this.user_input.confirmPassword &&
        this.user_input.password != "" &&
        this.user_input.confirmPassword != ""
      ) {
        return true;
      } else {
        return false;
        // alert('Register Success')
      }
    },
  },
  methods: {
    checkRegister() {
      if (!this.user_input.email) {
        alert("Email required");
        console.log("Email required");
      } else if (!this.validEmail(this.user_input.email.trim())) {
        alert("Email is not yet valid");
        console.log("Email is not yet valid");
      } else if (!this.validPassword(this.user_input.password)) {
        // alert('Weak password');
        console.log("Weak password");
      } else if (this.showMissmatch) {
        alert("miss match");
        console.log("miss match");
      } else {
        // add data to database
        this.addEmail();
        this.addPassword();
        this.$emit("pageReturn", 3);
      }
    },
    addEmail() {
      var usersEmail = [];
      usersEmail.push(this.user_input.email);
    },
    addPassword() {
      var usersPassword = [];
      usersPassword.push(this.user_input.password);
    },
    validEmail: function (email) {
      var re = /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/;
      return re.test(email);
    },
    validPassword: function (password) {
      this.password_length = password.length;
      const format = /[^A-Za-z0-9]/;
      if (this.password_length > 8) {
        this.contains_eight_characters = true;
      } else {
        this.contains_eight_characters = false;
      }
      this.contains_number = /\d/.test(password);
      this.contains_uppercase = /[A-Z]/.test(password);
      this.contains_special_character = format.test(password);

      if (
        this.contains_eight_characters === true &&
        this.contains_special_character === true &&
        this.contains_uppercase === true &&
        this.contains_number === true
      ) {
        return (this.valid_password = true);
      } else {
        if (this.contains_eight_characters === false) {
          alert("Password must have more than 8 characters");
        } else if (this.contains_uppercase === false) {
          alert("Password must have at least 1 uppercase");
        } else if (this.contains_number === false) {
          alert("Password must have at least 1 number");
        } else if (this.contains_special_character === false) {
          alert("Password must have at least 1 special characters");
        }
        return (this.valid_password = false);
      }
    },
    changeColor1() {
      let red = "colorRed";
      let green = "colorGreen";
      if (this.warningColor1 === true) {
        return green;
      }
      return red;
    },
    changeColor2() {
      let red = "colorRed";
      let green = "colorGreen";
      if (this.warningColor2 === true) {
        return green;
      }
      return red;
    },
    changeColor3() {
      let red = "colorRed";
      let green = "colorGreen";
      if (this.warningColor3 === true) {
        return green;
      }
      return red;
    },
    changeColor4() {
      let red = "colorRed";
      let green = "colorGreen";
      if (this.warningColor4 === true) {
        return green;
      }
      return red;
    },
    updateValue(event) {
      const value = event.target.value;
      const upper = /[A-Z]/.test(value);
      const number = /\d/.test(value);
      const format = /[^A-Za-z0-9]/;
      const special = format.test(value);
      if (String(value).length >= 8) {
        this.warningColor1 = true;
      } else {
        this.warningColor1 = false;
      }
      if (upper === true) {
        this.warningColor2 = true;
      } else {
        this.warningColor2 = false;
      }
      if (number === true) {
        this.warningColor3 = true;
      } else {
        this.warningColor3 = false;
      }
      if (special === true) {
        this.warningColor4 = true;
      } else {
        this.warningColor4 = false;
      }
    },
  },

  data() {
    return {
      warningColor1: false,
      warningColor2: false,
      warningColor3: false,
      warningColor4: false,
      user_database: {
        email: "",
        password: "",
      },
      user_input: {
        email: "",
        password: "",
        confirmPassword: "",
      },
      password_length: 0,
      contains_eight_characters: false,
      contains_number: false,
      contains_uppercase: false,
      contains_special_character: false,
      valid_password: false,
    };
  },
};
</script>

<style scoped>
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

.textDivider span {
  background: #282667;
  font-size: 26px;
  font-family: "CloudBold";
  padding: 0 10px;
  color: #ffffff;
}

#loginButton {
  color: #ffffff;
  border: none;
  width: 100%;
  margin-top: 10px;
  padding-top: 14px;
  padding-bottom: 14px;
  padding-left: 250px;
  padding-right: 250px;
  font-size: 30px;
  font-family: "CloudBold";
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

#right-side {
  background-color: #282667;
  display: flex;
  justify-content: center;
  align-items: top;
}

#left-side {
  background-color: #312e71;
  display: flex;
  justify-content: center;
  align-items: center;
}

.loginwith {
  font-size: 20px;
  font-family: "CloudLight";
  letter-spacing: 1.6px;
  color: #f9c0bd;
  margin-top: 10px;
  text-align: center;
  border-bottom: 2px solid #d5d5df;
  line-height: 0.1em;
  margin: 10px 0 20px;
}

.validatePassword {
  font-size: 20px;
  font-family: "CloudLight";
}

.fade-enter-active {
  transition: opacity 0.5s;
}

.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
}

.colorGreen {
  color: greenyellow;
}
.colorRed {
  color: red;
}
</style>
