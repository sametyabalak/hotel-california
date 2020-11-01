<template>
  <section id="activity">
    <v-container fluid>
      <v-row align="center" justify="center">
        <v-col cols="10">
          <v-row align="center" justify="center">
            <v-col cols="12" md="6" class="mx-auto">
              <h1 class="text-center font-weight-medium display-2 header">
                AKTİVİTELER
              </h1>
              <hr />
              <h1 class="text-center font-weight-light header">
                Muhteşem bir doğa manzarası kuş sesleri ve çakıllı yollarla
                çevrili otelimizde dağ ve dağ hayvanları ile yapılacak eşsiz
                aktivileter.
              </h1>
            </v-col>
            <!--  -->
          </v-row>
        </v-col>
        <v-col
          cols="12"
          md="3"
          sm="6"
          class="white--text text-center mx-auto"
          v-for="(value, key) in features"
          :key="key"
        >
          <v-avatar size="200px">
            <v-img
              alt="Avatar"
              style="
                border-style: solid;
                border-color: black;
                border-width: 8px;
              "
              :src="value.img"
            ></v-img>
          </v-avatar>
          <h1 class="text-center font-weight-medium">
            {{ value.title }}
          </h1>
          <h1 class="text-center font-weight-light">
            {{ value.text }}
          </h1>
        </v-col>
      </v-row>
      <v-row cols="12" md="6">
        <v-flex
          style="
            border: 1px solid rgba(255, 255, 255, 0.4);
            border-radius: 4px;
            border-width: 4px;
          "
          xs12
          offset-xs4
        >
          <br />
          <h1 class="otel ml-1">OTELİMİZ HANGİ DÖNEMLERDE AÇIK?</h1>
          <h1 class="font-weight-light otel ml-1">
            Otelimiz yılın 365 günü siz değerli misafirlerimize hitmez vermekte
            olup, aktiviteler mevsimlere göre farklılıklar göstermektedir. Lorem
            ipsum dolor sit amet, consectetur adipisicing elit. Aperiam eaque
            eum molestias neque non nulla?
          </h1>
        </v-flex>
      </v-row>
    </v-container>
    <!--  -->
    <section id="activity2">
      <v-container fluid>
        <v-row align="center" justify="center">
          <v-col cols="10">
            <v-row align="center" justify="center">
              <v-col cols="12" md="6" class="mx-auto">
                <h1 class="text-center font-weight-medium display-2 header2">
                  HANGİ MEVSİMDE HANGİ AKTİVİTE?
                </h1>
                <hr />
                <h1 class="text-center font-weight-light header2">
                  Aşağıdaki tabloda 4 mevsimde hangi aktivitelerin hangi oranda
                  yapılabileceğini görebilirsiniz.
                </h1>
              </v-col>
              <!--  -->
            </v-row>
          </v-col>
          <v-col
            cols="12"

            md="3"
            sm="6"
            class="white--text text-center mx-auto"
            v-for="(act, key) in activityRange"
            :key="key"
          >
            <v-progress-circular
              :rotate="360"
              :size="150"
              :width="15"
              :value="act.value"
              :color="act.color"
            >
              <h1 class="text-center font-weight-thin display-1 black--text">
                {{ act.value }} %
              </h1>
            </v-progress-circular>
            <h1 class="text-center font-weight-medium black--text">
              {{ act.title }}
            </h1>
            <h1 class="text-center black--text font-weight-light">
              {{ act.text }}
            </h1>
          </v-col>
        </v-row>
      </v-container>
    </section>
  </section>
</template>


<script>
export default {
  data() {
    return {
      features: [
        {
          img: require("@/assets/img/hiking.jpeg"),
          title: "DAĞ YÜRÜYÜŞÜ",
          text:
            "Lorem ipsum dolor sit amet consectetur adipisicing elit.Lorem ipsum dolor sit amet consectetur adipisicing elit.",
        },
        {
          img: require("@/assets/img/avcilik.jpg"),
          title: "AVCILIK",
          text:
            "Lorem ipsum dolor sit amet consectetur adipisicing elit.Lorem ipsum dolor sit amet consectetur adipisicing elit.",
        },
        {
          img: require("@/assets/img/bear.jpg"),
          title: "AYI TAKİBİ",
          text:
            "Lorem ipsum dolor sit amet consectetur adipisicing elit.Lorem ipsum dolor sit amet consectetur adipisicing elit.",
        },
        {
          img: require("@/assets/img/bird.jpg"),
          title: "KUŞ GÖÇLERİ",
          text:
            "Lorem ipsum dolor sit amet consectetur adipisicing elit.Lorem ipsum dolor sit amet consectetur adipisicing elit.",
        },
      ],
      activityRange: [
        {
          value: 90,
          title: "DAĞ YÜRÜYÜŞÜ",
          text: "4 Mevsim",
          color: "warning",
        },
        {
          value: 75,
          title: "AVCILIK",
          text: "Kış",
          color: "teal",
        },
        {
          value: 70,
          title: "AYI TAKİBİ",
          text: "İlkbahar, Yaz",
          color: "red",
        },
        {
          value: 85,
          title: "KUŞ GÖÇLERİ",
          text: "Sonbahar - İlkbahar",
          color: "green",
        },
      ],
    };
  },
};
</script>



<style scoped>
.otel {
  color: white;
}

.header {
  color: white;
}
.header2 {
  color: black;
}
#activity2 {
  background-color: #f5f5f5;
}
#activity {
  background-image: url("~@/assets/img/np.jpg");
  background-attachment: fixed;
  background-repeat: no-repeat;
  background-size: cover;
  background-position: center;
}

#activity .container,
#activity .row {
  height: 100%;
}
</style>
