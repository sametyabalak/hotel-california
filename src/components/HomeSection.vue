<template>
  <section id="home">
    <v-parallax dark src="@/assets/img/hotel5.jpg" height="750" class="hotel">
      <v-row align="center" justify="center">
        <v-col cols="10" class="text-center">
          <v-row align="center" justify="center">
            <v-col cols="12" md="12" xl="10">
              <h1 class="display-2 font-weight-medium mb-4 headerr">
                Hotel California
              </h1>
              <h1 class="font-weight-light headerr">
                Hey Merhaba!
                <!-- <br /> -->
                Hayatındaki en muhteşem tatil deneyimini yaşamaya, yeşilin ve
                beyazın muhteşem uyumuna tanıklık etmeye ve gizemlerle dolu bu
                dünyaya girmeye ne dersin?
                <br />
              </h1>
              <v-btn
                elevation="10"
                large
                @click="$vuetify.goTo('#about')"
                class="mt-8"
              >
                Otel Hakkında
                <v-icon class="ml-3">mdi-arrow-down</v-icon>
              </v-btn>
            </v-col>
            <v-col cols="12" md="6" xl="4" class="hidden-sm-and-down"> </v-col>
          </v-row>
        </v-col>
      </v-row>
      <div class="svg-border-waves text-white">
        <v-img src="@/assets/img/borderWaves.svg" />
      </div>
    </v-parallax>
    <v-container fluid id="features" class="mt-2">
      <v-row align="center" justify="center">
        <v-col cols="10">
          <v-row align="center" justify="space-around">
            <v-col cols="12" class="text-center">
              <h1 class="font-weight-light display-2">Neden Biz?</h1>
              <h1 class="font-weight-light">
                Lorem ipsum dolor sit amet consectetur adipisicing elit.
              </h1>
            </v-col>
            <v-col
              cols="12"
              sm="4"
              class="text-center"
              v-for="(feature, i) in features"
              :key="i"
            >
              <v-hover v-slot:default="{ hover }">
                <v-card
                  class="card"
                  shaped
                  :elevation="hover ? 10 : 4"
                  :class="{ up: hover }"
                >
                  <v-img
                    :src="feature.img"
                    max-width="250px"
                    max-height="130px"
                    class="d-block ml-auto mr-auto"
                    :class="{ 'zoom-efect': hover }"
                  ></v-img>
                  <h1 class="font-weight-regular">{{ feature.title }}</h1>
                  <h4 class="font-weight-regular subtitle-1">
                    {{ feature.text }}
                  </h4>
                </v-card>
              </v-hover>
            </v-col>
          </v-row>
        </v-col>
      </v-row>
    </v-container>
    <div class="svg-border-waves">
      <img src="~@/assets/img/wave2.svg" />
    </div>
  </section>
</template>

<script>
export default {
  data() {
    return {
      features: [
        {
          img: require("@/assets/img/easyway.jpg"),
          title: "Kolay Ulaşım",
          text: "Lorem ipsum dolor sit amet consectetur adipisicing elit.",
        },
        {
          img: require("@/assets/img/room.jpg"),
          title: "Konfor",
          text: "Lorem ipsum dolor sit amet consectetur adipisicing elit.",
        },
        {
          img: require("@/assets/img/mzr.jpg"),
          title: "Manzara",
          text: "Lorem ipsum dolor sit amet consectetur adipisicing elit.",
        },
      ],
    };
  },
};
</script>

<style lang="scss">
.headerr {
  text-shadow: 2px 2px black;
}
</style>

<style>
.svg-border-waves .v-image {
  position: absolute;
  bottom: 0;
  left: 0;
  height: 3rem;
  width: 100%;
  overflow: hidden;
}

#home {
  z-index: 0;
}
.svg-border-waves img {
  position: absolute;
  bottom: 0;
  left: 0;
  width: 100%;
  margin-bottom: -2px;
  z-index: -1;
}

.card {
  min-height: 300px;
  padding: 10px;
  transition: 0.5s ease-out;
}

.card .v-image {
  margin-bottom: 15px;
  transition: 0.75s;
}

.card h1 {
  margin-bottom: 10px;
}

.zoom-efect {
  transform: scale(1.1);
}

.up {
  transform: translateY(-20px);
  transition: 0.5s ease-out;
}
</style>

<style>
section {
  position: relative;
}
</style>
