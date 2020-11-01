<template>
  <section id="comments" class="pb-8">
    <v-container fluid>
      <v-row align="center" justify="center">
        <v-col cols="10">
          <v-row justify="center">
            <v-col cols="12" class="text-center">
              <h1 class="font-weight-light display-2">ZİYARETÇİ YORUMLARI</h1>
              <hr />
              <h1 class="font-weight-light">
                Aşağıda otelimizi ziyaret eden değerli misafirlerimizin
                yorumlarını bulabilirsiniz.
              </h1>
            </v-col>
          </v-row>
          <v-row v-for="i in 3" :key="i">
            <v-col v-for="(value, key) in comments" :key="key">
              <v-card class="mx-auto" outlined shaped elevation="5">
                <v-list-item three-line>
                  <v-list-item-avatar size="80">
                    <lottie-player
                      :src="value.img"
                      background="transparent"
                      speed="1"
                      style="width: 80px; height: 80px"
                      loop
                      autoplay
                    ></lottie-player>
                  </v-list-item-avatar>
                  <v-list-item-content>
                    <div class="overline mb-4">{{ value.name }}</div>

                    <h1 class="font-weight-light">"{{ value.comment }}"</h1>
                  </v-list-item-content>
                </v-list-item>
              </v-card>
            </v-col>
          </v-row>
        </v-col>
      </v-row>
    </v-container>
    <div class="svg-border-rounded text-light">
      <svg
        xmlns="http://www.w3.org/2000/svg"
        viewBox="0 0 1440 320"
        preserveAspectRatio="none"
        fill="currentColor"
      >
        <path
          d="M0,64L80,90.7C160,117,320,171,480,181.3C640,192,800,160,960,138.7C1120,117,1280,107,1360,101.3L1440,96L1440,320L1360,320C1280,320,1120,320,960,320C800,320,640,320,480,320C320,320,160,320,80,320L0,320Z"
        ></path>
      </svg>
    </div>
  </section>
</template>

<style lang="scss">
$main_color: #283e79;
</style>

<style scoped>
.header {
  background-color: #283e79;
  color: white;
}

.svg-border-rounded svg {
  position: absolute;
  bottom: 0;
  left: 0;
  width: 100%;
  color: #f4f7f5;
  z-index: -1;
}

#comments {
  z-index: 0;
}

.content {
  z-index: 1;
}
svg {
  overflow: hidden;
}
section {
  position: relative;
}
</style>

<script>
export default {
  data() {
    return {
      comments: [
        {
          img: "https://assets9.lottiefiles.com/packages/lf20_ojVIad.json",
          name: "EMILY GWENDSON",
          comment:
            "Lorem ipsum dolor sit amet consectetur adipisicing elit.Lorem ipsum dolor sit amet consectetur adipisicing elit.",
        },
        {
          img: "https://assets8.lottiefiles.com/private_files/lf30_6VfTTj.json",
          name: "ROBERT JULIAN",
          comment:
            "Lorem ipsum dolor sit amet consectetur adipisicing elit.Lorem ipsum dolor sit amet consectetur adipisicing elit.",
        },
      ],
    };
  },

  computed: {
    size() {
      const size = { md: "large", xl: "x-large" }[
        this.$vuetify.breakpoint.name
      ];
      return size ? { [size]: true } : {};
    },
    sizeText() {
      const size = {
        xs: "subtitle-1",
        sm: "text-h6",
        md: "text-h5",
        xl: "text-h4",
      }[this.$vuetify.breakpoint.name];
      console.log(size);
      return size ? { [size]: true } : {};
    },
  },
};
</script>
