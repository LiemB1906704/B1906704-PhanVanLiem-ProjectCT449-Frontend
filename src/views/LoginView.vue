<template lang="">
  <v-container>
    <v-row align="center" justify="center">
      <v-col cols="12" sm="8" md="8">
        <v-card class="elevation-12">
          <v-window v-model="step">
            <v-window-item :value="1">
              <v-row>
                <v-col cols="12" md="8">
                  <v-card-text class="mt-12">
                    <h1 class="text-center display-2 text-blue">
                      ĐĂNG NHẬP
                    </h1>
                    <div class="text-center mt-4">
                      <v-btn
                        icon="fab fa-facebook-f"
                        class="mx-2"
                        fab
                        color="white"
                        outlined
                        href="https://www.facebook.com/"
                        target="_blank"
                      >
                      </v-btn>

                      <v-btn
                        class="mx-2"
                        icon="fab fa-google-plus-g"
                        fab
                        color="white"
                        outlined
                        href="https://accounts.google.com"
                        target="_blank"
                      >
                      </v-btn>
                      <v-btn
                        icon="fab fa-linkedin-in"
                        class="mx-2"
                        fab
                        color="white"
                        outlined
                        href="https://www.linkedin.com/login?fromSignIn=true&trk=guest_homepage-basic_nav-header-signin"
                        target="_blank"
                      >
                      </v-btn>
                    </div>
                    
                    <v-form
                      ref="form"
                      enctype="multipart/form-data"
                      @submit.prevent="submitFormUser"
                    >
                      <v-text-field
                        label="Email"
                        :rules="rules"
                        name="Email"
                        prepend-icon="mdi:mdi-email"
                        type="email"
                        color="blue"
                        variant="underlined"
                        v-model="user.email"
                      />

                      <v-text-field
                        id="password"
                        label="Password"
                        name="password"
                        prepend-icon="mdi:mdi-lock"
                        type="password"
                        variant="underlined"
                        :rules="rules"
                        color="blue"
                        autocomplete="on"
                        v-model="user.password"
                      />
                      <v-card flat class="text-center">
                        <v-btn
                          type="submit"
                          rounded
                          color="blue mb-3"
                          dark
                          >ĐĂNG NHẬP
                        </v-btn>
                      </v-card>
                    </v-form>
                  </v-card-text>
                </v-col>
                <v-col cols="12" md="4" class="bg-blue">
                  <v-card-text class="text-white mt-12">
                    <h1 class="text-center display-1 mb-3">Đăng ký</h1>
                    <h5 class="text-center">
                      Vui lòng Đăng ký nếu bạn chưa có tài khoản!
                    </h5>
                  </v-card-text>

                  <div class="text-center text-black">
                    <v-btn class="mb-3" rounded outlined dark @click="step++">
                        Đăng ký
                    </v-btn>
                  </div>
                </v-col>
              </v-row>
            </v-window-item>
            <v-window-item :value="2">
              <v-row class="fill-height">
                <v-col cols="12" md="4" class="bg-blue">
                  <v-card-text class="text-white mt-12">
                    <h1 class="text-center display-1 mb-4 lh-24">
                      Đăng nhập
                    </h1>
                    <h5 class="text-center">
                      Vui lòng Đăng nhập nếu bạn đã có tài khoản!
                    </h5>
                  </v-card-text>
                  <div class="text-center text-black">
                    <v-btn ref="btnSU" rounded outlined dark @click="step--"
                      >Đăng nhập
                    </v-btn>
                  </div>
                </v-col>

                <v-col cols="12" md="8">
                  <v-card-text class="mt-12">
                    <h1 class="text-center display-2 text-blue">
                      TẠO TÀI KHOẢN MỚI
                    </h1>
                    <div class="text-center mt-4">
                      <v-btn
                        icon="fab fa-facebook-f"
                        class="mx-2"
                        fab
                        color="white"
                        outlined
                        href="https://www.facebook.com/"
                        target="_blank"
                      >
                      </v-btn>

                      <v-btn
                        class="mx-2"
                        icon="fab fa-google-plus-g"
                        fab
                        color="white"
                        outlined
                        href="https://accounts.google.com"
                        target="_blank"
                      >
                      </v-btn>
                      <v-btn
                        icon="fab fa-linkedin-in"
                        class="mx-2"
                        fab
                        color="white"
                        outlined
                        href="https://www.linkedin.com/login?fromSignIn=true&trk=guest_homepage-basic_nav-header-signin"
                        target="_blank"
                      >
                      </v-btn>
                    </div>
                    
                    <v-form @submit.prevent="submitFormUserRegister">
                      <v-text-field
                        v-model="userRegister.name"
                        :rules="rules"
                        label="Name"
                        name="Name"
                        prepend-icon="fa-solid fa-user"
                        variant="underlined"
                        type="text"
                        color="blue"
                      />
                      <v-text-field
                        v-model="userRegister.email"
                        :rules="rules"
                        label="Email"
                        name="Email"
                        variant="underlined"
                        prepend-icon="mdi:mdi-email"
                        type="text"
                        color="blue"
                      />

                      <v-text-field
                        v-model="userRegister.password"
                        :rules="rules"
                        id="password"
                        label="Password"
                        name="password"
                        variant="underlined"
                        prepend-icon="mdi:mdi-lock"
                        autocomplete="on"
                        type="password"
                        color="blue"
                      />
                      <v-card flat class="text-center">
                        <v-btn
                          type="submit"
                          rounded
                          color="blue mb-3"
                          dark
                        >
                          ĐĂNG KÝ
                        </v-btn>
                      </v-card>
                    </v-form>
                  </v-card-text>
                </v-col>
              </v-row>
            </v-window-item>
          </v-window>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>
<script>
import API from "../api";
import store from "../store/store";
export default {
  name: "LoginView",
  data() {
    return {
      rules: [(value) => !!value || "This field is require"],
      user: {
        email: "",
        password: "",
      },
      userRegister: {
        name: "",
        email: "",
        password: "",
      },
      step: 1,
    };
  },
  methods: {
    async submitFormUser() {
      try {
        await API.loginUser(this.user);
        store.dispatch("setAuthUser", true);
        store.commit("SET_CLICK_BTN");
      } catch (error) {
        this.$toast.error(error.response.data.message, {
          position: "top-right",
        });
        store.dispatch("setAuthUser", false);
      }
    },
    async submitFormUserRegister() {
      try {
        const res = await API.registerUser(this.userRegister);
        if (res) {
          this.$refs.btnSU.$el.click();
        }
        this.$toast.success(res.message, {
          position: "top-right",
        });
      } catch (error) {
        this.$toast.error("failed to register", {
          position: "top-right",
        });
      }
    },
  },
};
</script>
<style lang=""></style>
