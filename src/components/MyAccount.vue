<template>
  <div id="myaccount">
    <h1 class="title">MY ACCOUNT</h1>

    <!-- Bar -->
    <div
      style="
        margin-top: 30px;
        width: 100%;
        display: grid;
        grid-template-columns: 15% 20% 65%;
      "
    >
      <h2 style="padding-left: 40px" class="bartext">Profile</h2>
      <h2 @click="OnclickChange()" class="bartext">Change Password</h2>
    </div>
    <!-- Bar -->

    <!-- Bar -->
    <div style="margin-top: 2px">
      <hr style="display: inline-block; width: 11%" class="line_select" />
      <hr style="display: inline-block; width: 20%" class="line" />
      <hr style="display: inline-block; width: 67%" class="line" />
    </div>
    <!-- Bar -->

    <!-- Profile -->
    <div
      style="
        margin-top: 63px;
        width: 100%;
        display: grid;
        grid-template-columns: 20% 80%;
      "
    >
      <!-- Profile Pic-->
      <div style="position: relative; left: 0; top: 0">
        <img
          class="profilepic"
          style="
            position: relative;
            top: 0;
            left: 0;
            margin-top: 1px;
            margin-left: 1px;
            width: 229px;
          "
          src="@/assets/user/profile.jpg"
        />
        <img
          class="profilepic"
          style="position: absolute; top: 0px; left: 0px; width: 232px"
          src="@/assets/user/maskfix.png"
        />
      </div>
      <!-- Profile Pic-->

      <!-- Input -->
      <div style="margin-left: 30px">
        <!-- General -->
        <div class="box" style="padding: 25px">
          <h1 class="inputHead">GENERAL</h1>
          <div style="margin-top: 20px; margin-left: 25px">
            <!-- Input Container -->
            <div
              style="width: 100%; display: grid; grid-template-columns: 50% 50%"
            >
              <div
                style="
                  width: 100%;
                  align-items: center;
                  justify-content: center;
                  display: grid;
                  grid-template-columns: 30% 70%;
                "
              >
                <h3 class="inputText">FIRST NAME</h3>
                <input
                  v-if="editSelect == false"
                  style="margin-left: 20px; width: 85%"
                  class="input"
                  type="text"
                  v-model="profile.firstName"
                  disabled
                />
                <input
                  v-else
                  style="
                    border-bottom: 2px solid #312f71;
                    margin-left: 20px;
                    width: 85%;
                  "
                  class="input"
                  type="text"
                  ref="firstName"
                  :value="profile.firstName"
                />
              </div>
              <div
                style="
                  margin-left: 10px;
                  width: 100%;
                  align-items: center;
                  justify-content: center;
                  display: grid;
                  grid-template-columns: 30% 70%;
                "
              >
                <h3 class="inputText">BIRTH DATE</h3>
                <input
                  v-if="editSelect == false"
                  style="margin-left: 20px; width: 85%"
                  class="input"
                  type="text"
                  v-model="connectDate"
                  disabled
                />
                <div v-else style="margin-left: 20px">
                  <v-select
                    :options="getDayList()"
                    :clearable="false"
                    :searchable="false"
                    ref="birthday_day"
                    class="style-chooser"
                    style="display: inline-block; width: 26%"
                    v-model="day"
                    placeholder="day"
                  ></v-select>
                  <v-select
                    :options="months"
                    :clearable="false"
                    :searchable="false"
                    ref="birthday_month"
                    class="style-chooser"
                    style="margin-left: 10px; display: inline-block; width: 33%"
                    :reduce="(abbreMonth) => abbreMonth.fullMonth"
                    v-model="month"
                    label="abbreMonth"
                    placeholder="month"
                  ></v-select>
                  <v-select
                    :options="getYearList()"
                    :clearable="false"
                    :searchable="false"
                    ref="birthday_year"
                    class="style-chooser"
                    style="margin-left: 10px; display: inline-block; width: 34%"
                    v-model="year"
                    placeholder="year"
                  ></v-select>
                </div>
              </div>
            </div>
            <!-- Input Container -->

            <!-- Input Container -->
            <div
              style="
                margin-top: 25px;
                width: 100%;
                display: grid;
                grid-template-columns: 50% 50%;
              "
            >
              <div
                style="
                  width: 100%;
                  align-items: center;
                  justify-content: center;
                  display: grid;
                  grid-template-columns: 30% 70%;
                "
              >
                <h3 class="inputText">LAST NAME</h3>
                <input
                  v-if="editSelect == false"
                  style="margin-left: 20px; width: 85%"
                  class="input"
                  type="text"
                  v-model="profile.lastName"
                  disabled
                />
                <input
                  v-else
                  style="
                    border-bottom: 2px solid #312f71;
                    margin-left: 20px;
                    width: 85%;
                  "
                  class="input"
                  type="text"
                  ref="lastName"
                  :value="profile.lastName"
                />
              </div>
              <div
                style="
                  margin-left: 10px;
                  width: 100%;
                  align-items: center;
                  justify-content: center;
                  display: grid;
                  grid-template-columns: 30% 70%;
                "
              >
                <h3 class="inputText">CPE</h3>
                <input
                  v-if="editSelect == false"
                  style="margin-left: 20px; width: 85%"
                  class="input"
                  type="text"
                  v-model="profile.cpe"
                  disabled
                />
                <v-select
                  v-else
                  :clearable="false"
                  :options="classList()"
                  ref="cpe"
                  :searchable="false"
                  class="style-chooser"
                  style="margin-left: 20px; width: 40%"
                  v-model="cpe"
                  placeholder="CPE"
                ></v-select>
              </div>
            </div>
            <!-- Input Container -->

            <!-- Input Container -->
            <div
              style="
                margin-top: 25px;
                margin-bottom: 30px;
                width: 100%;
                display: grid;
                grid-template-columns: 50% 50%;
              "
            >
              <div
                style="
                  width: 100%;
                  align-items: center;
                  justify-content: center;
                  display: grid;
                  grid-template-columns: 30% 70%;
                "
              >
                <h3 class="inputText">NICKNAME</h3>
                <input
                  v-if="editSelect == false"
                  style="margin-left: 20px; width: 85%"
                  class="input"
                  type="text"
                  v-model="profile.nickName"
                  disabled
                />
                <input
                  v-else
                  style="
                    border-bottom: 2px solid #312f71;
                    margin-left: 20px;
                    width: 85%;
                  "
                  class="input"
                  type="text"
                  ref="nickName"
                  :value="profile.nickName"
                />
              </div>
            </div>
            <!-- Input Container -->
          </div>
        </div>

        <!-- Second Section -->
        <div
          style="
            margin-top: 25px;
            margin-bottom: 30px;
            width: 100%;
            display: grid;
            grid-template-columns: 50% 50%;
          "
        >
          <div class="box" style="padding: 25px; margin-right: 12px">
            <h1 class="inputHead">CONTACT</h1>
            <div style="margin-top: 20px; margin-left: 25px">
              <!-- Input Container -->
              <div
                style="
                  margin-top: 25px;
                  width: 100%;
                  display: grid;
                  grid-template-columns: 100%;
                "
              >
                <div
                  style="
                    width: 100%;
                    align-items: center;
                    justify-content: center;
                    display: grid;
                    grid-template-columns: 40% 60%;
                  "
                >
                  <h3 class="inputText">PHONE</h3>
                  <input
                    v-if="editSelect == false"
                    style="margin-left: 30px; width: 85%"
                    class="input"
                    type="text"
                    v-model="profile.phone"
                    disabled
                  />
                  <input
                    v-else
                    style="
                      border-bottom: 2px solid #312f71;
                      margin-left: 30px;
                      width: 85%;
                    "
                    class="input"
                    type="number"
                    ref="phone"
                    @input="updateValue"
                    :value="phone"
                  />
                </div>
              </div>
              <!-- Input Container -->

              <!-- Input Container -->
              <div
                style="
                  margin-top: 25px;
                  width: 100%;
                  display: grid;
                  grid-template-columns: 100%;
                "
              >
                <div
                  style="
                    width: 100%;
                    align-items: center;
                    justify-content: center;
                    display: grid;
                    grid-template-columns: 40% 60%;
                  "
                >
                  <h3 class="inputText">LINE</h3>
                  <input
                    v-if="editSelect == false"
                    style="margin-left: 30px; width: 85%"
                    class="input"
                    type="text"
                    v-model="profile.line"
                    disabled
                  />
                  <input
                    v-else
                    style="
                      border-bottom: 2px solid #312f71;
                      margin-left: 30px;
                      width: 85%;
                    "
                    class="input"
                    ref="line"
                    type="text"
                    :value="profile.line"
                  />
                </div>
              </div>
              <!-- Input Container -->

              <!-- Input Container -->
              <div
                style="
                  margin-top: 25px;
                  width: 100%;
                  display: grid;
                  grid-template-columns: 100%;
                "
              >
                <div
                  style="
                    width: 100%;
                    align-items: center;
                    justify-content: center;
                    display: grid;
                    grid-template-columns: 40% 60%;
                  "
                >
                  <h3 class="inputText">FACEBOOK</h3>
                  <input
                    v-if="editSelect == false"
                    style="margin-left: 30px; width: 85%"
                    class="input"
                    type="text"
                    v-model="profile.facebook"
                    disabled
                  />
                  <input
                    v-else
                    style="
                      border-bottom: 2px solid #312f71;
                      margin-left: 30px;
                      width: 85%;
                    "
                    class="input"
                    ref="facebook"
                    type="text"
                    :value="profile.facebook"
                  />
                </div>
              </div>
              <!-- Input Container -->
            </div>
          </div>

          <div class="box" style="padding: 25px; margin-left: 12px">
            <h1 class="inputHead">WORK</h1>
            <div style="margin-top: 20px; margin-left: 25px">
              <!-- Input Container -->
              <div
                style="
                  margin-top: 25px;
                  width: 100%;
                  display: grid;
                  grid-template-columns: 100%;
                "
              >
                <div
                  style="
                    width: 100%;
                    align-items: center;
                    justify-content: center;
                    display: grid;
                    grid-template-columns: 40% 60%;
                  "
                >
                  <h3 class="inputText">ORGANIZATION</h3>
                  <input
                    v-if="editSelect == false"
                    style="margin-left: 30px; width: 85%"
                    class="input"
                    type="text"
                    v-model="profile.organ"
                    disabled
                  />
                  <input
                    v-else
                    style="
                      border-bottom: 2px solid #312f71;
                      margin-left: 30px;
                      width: 85%;
                    "
                    class="input"
                    ref="organ"
                    type="text"
                    :value="profile.organ"
                  />
                </div>
              </div>
              <!-- Input Container -->

              <!-- Input Container -->
              <div
                style="
                  margin-top: 25px;
                  width: 100%;
                  display: grid;
                  grid-template-columns: 100%;
                "
              >
                <div
                  style="
                    width: 100%;
                    align-items: center;
                    justify-content: center;
                    display: grid;
                    grid-template-columns: 40% 60%;
                  "
                >
                  <h3 class="inputText">ROLE</h3>
                  <input
                    v-if="editSelect == false"
                    style="margin-left: 30px; width: 85%"
                    class="input"
                    type="text"
                    v-model="profile.role"
                    disabled
                  />
                  <input
                    v-else
                    style="
                      border-bottom: 2px solid #312f71;
                      margin-left: 30px;
                      width: 85%;
                    "
                    class="input"
                    ref="role"
                    type="text"
                    :value="profile.role"
                  />
                </div>
              </div>
              <!-- Input Container -->

              <!-- Input Container -->
              <div
                style="
                  margin-top: 25px;
                  width: 100%;
                  display: grid;
                  grid-template-columns: 100%;
                "
              >
                <div
                  style="
                    width: 100%;
                    align-items: center;
                    justify-content: center;
                    display: grid;
                    grid-template-columns: 40% 60%;
                  "
                >
                  <h3 class="inputText">FIELD</h3>
                  <input
                    v-if="editSelect == false"
                    style="margin-left: 30px; width: 85%"
                    class="input"
                    type="text"
                    v-model="profile.field"
                    disabled
                  />
                  <input
                    v-else
                    style="
                      border-bottom: 2px solid #312f71;
                      margin-left: 30px;
                      width: 85%;
                    "
                    class="input"
                    ref="field"
                    type="text"
                    :value="profile.field"
                  />
                </div>
              </div>
              <!-- Input Container -->
            </div>
          </div>
        </div>
        <!-- Second Section -->

        <!-- Button -->
        <div id="button">
          <!-- Edit -->
          <div v-show="!editSelect">
            <button @click="editSelect = true" class="white_button">
              EDIT PROFILE
            </button>
          </div>

          <!-- Save/Cancle -->
          <div v-show="editSelect">
            <button
              @click="saveProfile()"
              style="margin-right: 30px"
              class="pink_button"
            >
              SAVE CHANGE
            </button>
            <button
              @click="
                cancel();
                editSelect = false;
              "
              class="white_button"
            >
              CANCLE
            </button>
          </div>
        </div>
        <!-- Button -->
      </div>
      <!-- Input -->
    </div>
    <!-- Profile -->
  </div>
</template>

<script>
import Vue from "vue";
import vSelect from "vue-select";
Vue.component("v-select", vSelect);
import "vue-select/dist/vue-select.css";

export default {
  data() {
    return {
      img: require("@/assets/user/profile.jpg"),
      selected_pro: true,
      selected_change: false,
      editSelect: false,
      day: "",
      month: "",
      year: "",
      cpe: "",
      phone: "",
      connectDate: "",
      profile: {
        id: "1",
        password: "Passw0rd",
        firstName: "Worachot",
        lastName: "Yuwamirt",
        nickName: "Bm",
        birthday_day: "12",
        birthday_month: "December",
        birthday_year: "2020",
        cpe: "33",
        phone: "0819675607",
        line: "Bmskx",
        facebook: "Bm worachot",
        organ: "CPENight.corp",
        role: "Developer",
        field: "Front-end",
        photo: "",
        address: "KMUTT",
      },
      months: [
        { fullMonth: "January", abbreMonth: "JAN" },
        { fullMonth: "February", abbreMonth: "FEB" },
        { fullMonth: "March", abbreMonth: "MAR" },
        { fullMonth: "April", abbreMonth: "APR" },
        { fullMonth: "May", abbreMonth: "MAY" },
        { fullMonth: "June", abbreMonth: "JUN" },
        { fullMonth: "July", abbreMonth: "JUL" },
        { fullMonth: "August", abbreMonth: "AUG" },
        { fullMonth: "September", abbreMonth: "SEP" },
        { fullMonth: "October", abbreMonth: "OCT" },
        { fullMonth: "November", abbreMonth: "NOV" },
        { fullMonth: "December", abbreMonth: "DEC" },
      ],
    };
  },
  computed: {
    selectedProfile() {
      let selected = "line_select";
      let deselected = "line";
      if (this.selected_pro === true) {
        return selected;
      }
      return deselected;
    },
    selectedChangedPassword() {
      let selected = "line_select";
      let deselected = "line";
      if (this.selected_change === true) {
        return selected;
      }
      return deselected;
    },
  },
  mounted() {
    this.day = this.profile.birthday_day;
    this.month = this.profile.birthday_month;
    this.year = this.profile.birthday_year;
    this.cpe = this.profile.cpe;
    this.phone = this.profile.phone;
    this.connectDate =
      this.profile.birthday_day +
      " " +
      this.profile.birthday_month +
      " " +
      this.profile.birthday_year;
  },
  methods: {
    saveProfile() {
      this.profile.firstName = this.$refs["firstName"].value;
      this.profile.lastName = this.$refs["lastName"].value;
      this.profile.nickName = this.$refs["nickName"].value;
      this.profile.birthday_day = this.day;
      this.profile.birthday_month = this.month;
      this.profile.birthday_year = this.year;
      this.profile.cpe = this.cpe;
      this.profile.phone = this.$refs["phone"].value;
      this.profile.line = this.$refs["line"].value;
      this.profile.facebook = this.$refs["facebook"].value;
      this.profile.organ = this.$refs["organ"].value;
      this.profile.role = this.$refs["role"].value;
      this.profile.field = this.$refs["field"].value;
      this.connectDate =
        this.profile.birthday_day +
        " " +
        this.profile.birthday_month +
        " " +
        this.profile.birthday_year;
      this.editSelect = !this.editSelect;
    },
    cancel() {
      this.day = this.profile.birthday_day;
      this.month = this.profile.birthday_month;
      this.year = this.profile.birthday_year;
      this.cpe = this.profile.cpe;
      this.phone = this.profile.phone;
    },
    getDayList() {
      var dayList = [];

      for (var i = 1; i <= 31; i++) {
        dayList.push(i);
      }

      return dayList;
    },
    getYearList() {
      var yearList = [];

      for (var i = 1920; i <= 2020; i++) {
        yearList.push(i);
      }

      return yearList;
    },
    classList() {
      var classList = ["อาจารย์", "บุคคลากร"];

      for (var i = 1; i <= 34; i++) {
        classList.push("CPE " + i);
      }

      return classList;
    },
    OnclickChange() {
      this.$emit("selectReturn", false);
    },
    updateValue(event) {
      const value = event.target.value;
      if (String(value).length <= 10) {
        this.phone = value;
      }
      this.$forceUpdate();
    },
  },
};
</script>

<style scoped>
#button {
  float: right;
  margin-top: 25px;
}

.white_button {
  letter-spacing: 2.24px;
  font-size: 28px;
  color: #312f71;
  border: 3px solid #312f71;
  padding-top: 15px;
  padding-bottom: 15px;
  padding-left: 34px;
  padding-right: 34px;
  background-color: transparent;
  font-family: "CloudBold";
}

.pink_button {
  letter-spacing: 2.24px;
  font-size: 28px;
  background-color: #f98394;
  color: #ffffff;
  border: 3px solid #f98394;
  padding-top: 15px;
  padding-bottom: 15px;
  padding-left: 34px;
  padding-right: 34px;
  font-family: "CloudBold";
}

input[type="text"] {
  color: #312f71;
  font-size: 25px;
  letter-spacing: 2px;
  font-family: "CloudBold";
}

input[type="text"]:focus {
  border: none;
  background-color: none;
  outline: 0;
}

input[type="number"] {
  color: #312f71;
  font-size: 25px;
  letter-spacing: 2px;
  font-family: "CloudBold";
}

input[type="number"]:focus {
  border: none;
  background-color: none;
  outline: 0;
}

.input {
  background: transparent;
  border: none;
  /* border-bottom: 1px solid black; */
}

input[data-v-7ecbf6ee] {
  margin: 0px;
  padding-left: 10px;
  background: transparent;
  border: none;
  width: 100%;
}

.inputHead {
  color: #312f71;
  letter-spacing: 1.92px;
  font-family: "CloudBold";
  font-size: 24px;
  margin: 0;
}

.inputText {
  color: #312f71;
  letter-spacing: 1.6px;
  font-family: "CloudBold";
  font-size: 20px;
  margin: 0;
}

.box {
  border: 3px solid #312f71;
}
#myaccount {
  background-color: #ffffff;
  padding-top: 65px;
  padding-left: 108px;
  padding-right: 130px;
}

.title {
  color: #312f71;
  letter-spacing: 6px;
  font-family: "CloudBold";
  font-size: 60px;
  margin: 0;
}

.bartext {
  color: #312f71;
  letter-spacing: 2.2px;
  font-family: "CloudBold";
  font-size: 22px;
  margin: 0;
}

.line {
  border: 1.5px solid #312f71;
  background-color: #312f71;
  opacity: 0.3;
  margin-bottom: 3px;
}

.line_select {
  border: 5px solid #f98394;
  background-color: #f98394;
  opacity: 1;
  margin: 0;
}
</style>