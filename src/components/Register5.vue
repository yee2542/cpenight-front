<template>
  <div id="Register5">
    <div
      class="row"
      style="min-height: 100vh; display: grid; grid-template-columns: 37% 63%"
    >
      <div id="left-side">
        <img style="height: 537px" src="@/assets/Logo.png" />
      </div>
      <div id="right-side" class="column">
        <div>
          <div style="display: grid; grid-template-columns: 60% 40%">
            <div>
              <h1 class="title" style="margin: 0px">Please tell us</h1>
              <h1 class="title" style="margin: 0px">more about yourself.</h1>
            </div>
            <div>
              <img
                style="width: 130px; padding-left: 231px"
                src="@/assets/Group 299.png"
              />
            </div>
          </div>

          <div>
            <!-- Second Section-->
            <h2 style="margin-top: 35px">Where do you work?</h2>
            <div
              class="row"
              style="display: grid; grid-template-columns: 50% 50%"
            >
              <div>
                <!-- Input Section -->
                <div style="padding-right: 33px">
                  <h1 class="inputText">ORGANIZATION</h1>
                  <div style="margin-top: 20px; padding-right: 10px">
                    <input
                      style="margin: 0px; width: 100%"
                      class="input"
                      type="text"
                      v-model="organ"
                      placeholder="Enter your organization name"
                    />
                  </div>
                  <hr
                    style="
                      margin-top: 10px;
                      margin-bottom: 30px;
                      height: 2px;
                      border: none;
                      color: #ffffff;
                      background-color: #ffffff;
                    "
                  />
                </div>
              </div>

              <div>
                <!-- Input Section -->
                <div style="padding-right: 33px">
                  <h1 class="inputText">ROLE</h1>
                  <div style="margin-top: 20px; padding-right: 10px">
                    <input
                      style="margin: 0px; width: 100%"
                      class="input"
                      type="text"
                      v-model="role"
                      placeholder="Enter your role (e.g. Manager)"
                    />
                  </div>
                  <hr
                    style="
                      margin-top: 10px;
                      margin-bottom: 30px;
                      height: 2px;
                      border: none;
                      color: #ffffff;
                      background-color: #ffffff;
                    "
                  />
                </div>
                <!-- Input Section -->
              </div>
            </div>

            <!-- First Section-->
            <h2 style="margin-top: 35px">What do you do?</h2>
            <div
              class="row"
              style="display: grid; grid-template-columns: 50% 50%"
            >
              <div>
                <!-- Input Section -->
                <div style="padding-right: 33px">
                  <h1 class="inputText">FIELD OF WORK</h1>
                  <div style="margin-top: 20px; padding-right: 10px">
                    <input
                      style="margin: 0px; width: 100%"
                      class="input"
                      type="text"
                      v-model="field"
                      placeholder="Enter your field (e.g. UX/UI Designer)"
                    />
                  </div>
                  <hr
                    style="
                      margin-top: 10px;
                      margin-bottom: 90px;
                      height: 2px;
                      border: none;
                      color: #ffffff;
                      background-color: #ffffff;
                    "
                  />
                </div>
              </div>

              <div></div>
            </div>
          </div>
          <link
            rel="stylesheet"
            href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.7.0/css/font-awesome.min.css"
          />
          <div
            class="row"
            style="
              margin-top: 68px;
              display: grid;
              grid-template-columns: 50% 50%;
            "
          >
            <div>
              <button id="backButton" @click="backPage()">
                <i
                  style="align: center; padding-right: 20px"
                  class="fa fa-arrow-left"
                ></i
                >BACK
              </button>
            </div>
            <div>
              <button id="nextButton" @click="nextPage()">
                FINISH<i
                  style="align: center; padding-left: 20px"
                  class="fa fa-arrow-right"
                ></i>
              </button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Register5",
  components: {},
  data() {
    return {};
  },
  methods: {
    nextPage() {
      alert("Register Success");
      window.location.href = "/login";
    },
    backPage() {
      this.$emit("pageReturn", 4);
    },
  },
};
</script>

<style scoped>
input[type="text"]:focus {
  border: none;
  background-color: none;
  outline: 0;
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
  letter-spacing: 1.6px;
  font-family: "CloudLight";
  opacity: 0.7;
}

input[data-v-7ecbf6ee] {
  margin: 0px;
  padding-left: 10px;
  background: transparent;
  border: none;
  width: 100%;
}

input[type="password"] {
  color: white;
  font-size: 26px;
  letter-spacing: 1.6px;
  font-family: "CloudLight";
  opacity: 0.7;
}

.inputText {
  font-family: "CloudLight";
  letter-spacing: 1.6px;
  color: #ffffff;
  opacity: 0.7;
  font-size: 20px;
}

.textDivider span {
  background: #282667;
  font-size: 26px;
  font-family: "CloudBold";
  padding: 0 10px;
  color: #ffffff;
}

#nextButton {
  color: #ffffff;
  background: #f28093;
  border: none;
  padding-top: 15px;
  padding-bottom: 15px;
  padding-left: 32px;
  padding-right: 32px;
  font-size: 28px;
  font-family: "CloudBold";
  margin-left: 240px;
}

#backButton {
  color: #ffffff;
  border: 3px solid #ffffff;
  background-color: transparent;
  padding-top: 15px;
  padding-bottom: 15px;
  padding-left: 32px;
  padding-right: 32px;
  font-size: 28px;
  font-family: "CloudBold";
}

::placeholder {
  color: #ffffff;
  font-size: 20px;
  font-family: "CloudLight";
  opacity: 0.7;
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

.title {
  font-size: 44px;
  font-family: "CloudBold";
  letter-spacing: 4.4px;
  color: #ffffff;
  z-index: 2;
}

h2 {
  text-align: left;
  font-family: "CloudBold";
  letter-spacing: 3px;
  color: #ffffff;
  font-size: 30px;
}

#right-side {
  background-color: #282667;
  display: flex;
  justify-content: center;
  align-items: center;
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
  margin-top: 0px;
}
</style>