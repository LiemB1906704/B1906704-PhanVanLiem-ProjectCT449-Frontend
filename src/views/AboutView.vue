<template>
  <v-container fluid class="bg-blue-grey-darken-4 h-100 d-flex align-center">
    <v-row>
      <v-col cols="12" sm="12" md="7" class="pt-0">
        <h1>ABOUT US</h1>

        <p class="text-justify fs-24">
          Đây là trang web giúp các bạn tổng hợp lại các nhân vật trong phim
          hoạt hình mà các bạn yêu thích được xây dựng bằng Vue.js và Node.js dùng cơ cơ sở dữ liệu Mongodb.
        </p>
        <p>
          Liên hệ để biết thêm thông tin chi tiết.
        </p>

        <v-timeline align="start" class="h-50">
          <v-timeline-item
            v-for="(item, i) in items"
            :key="i"
            :dot-color="item.color"
            size="small"
          >
            <template v-slot:opposite>
              <div
                :class="`pt-1 headline font-weight-bold text-${item.color}`"
                v-text="item.description"
              ></div>
            </template>
            <div>
              <h2
                :class="`pt-1 headline font-weight-light mb-4 text-${item.color}`"
              >
                {{ item.text }}
              </h2>
            </div>
          </v-timeline-item>
        </v-timeline>
        <div class="mt-4">
          <v-btn
            icon="fab fa-facebook-f"
            class="mx-2"
            fab
            color="blue"
            outlined
            href="https://www.facebook.com/"
            target="_blank"
          >
          </v-btn>

          <v-btn
            class="mx-2"
            icon="fab fa-google-plus-g"
            fab
            color="blue"
            outlined
            href="https://accounts.google.com"
            target="_blank"
          >
          </v-btn>
          <v-btn
            icon="fab fa-linkedin-in"
            class="mx-2"
            fab
            color="blue"
            outlined
            href="https://www.linkedin.com/login?fromSignIn=true&trk=guest_homepage-basic_nav-header-signin"
            target="_blank"
          >
          </v-btn>
        </div>
      </v-col>
      <v-col cols="12" sm="12" md="5" class="bg-white pa-0">
        <v-carousel>
          <v-carousel-item
            src="https://www.ctu.edu.vn/images/2022/08/12/hitech-2.jpg"
            cover
          ></v-carousel-item>

          <v-carousel-item
            src="https://www.ctu.edu.vn/images/upload/news/2022/lkg222321.jpg"
            cover
          ></v-carousel-item>

          <v-carousel-item
            src="https://reviewedu.net/wp-content/uploads/2021/09/truong-dai-hoc-can-tho-ctu.jpg"
            cover
          ></v-carousel-item>
        </v-carousel>
      </v-col>
    </v-row>
  </v-container>
</template>
<script>
export default {
  data: () => ({
    items: [
      {
        color: "light-blue",
        description: "Trường",
        text: "CNTT Và Truyền Thông",
      },
      {
        color: "light-blue",
        description: "Trực Thuộc",
        text: "Đại Học Cần Thơ",
      },
      {
        color: "light-blue",
        description: "Ngành",
        text: "Kỹ Thuật Phần Mềm",
      },
    ],
  }),
};
</script>
