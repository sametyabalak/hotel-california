<template>
  <section class="pb-8" id="contact">
    <v-container fluid>
      <v-row align="center" justify="center">
        <v-col cols="10">
          <v-row justify="center">
            <v-col cols="12" sm="5">
              <h1 class="font-weight-light display-1">
                Bizimle İletişime Geçin
              </h1>
              <h3 class="font-weight-light mt-3">
                Sizlerde formu doldurarak Hotel California'da tatil yapma
                keyfini çıkarabilirsiniz. :)
                <br />
                Daha fazla bilgi için lütfen arayınız...
              </h3>
              <h3 class="font-weight-light mt-3">
                Telefon: <a href="tel://+905537434305">+905537434305</a>
              </h3>
              <h3 class="font-weight-light">
                Email:
                <a href="mailto://sametyabalak@outlook.com"
                  >sametyabalak@outlook.com</a
                >
              </h3>
              <v-container class="mx-auto">
                <lottie-player
                  src="https://assets8.lottiefiles.com/datafiles/7JozmEN9dibUFg4/data.json"
                  background="transparent"
                  speed="1"
                  style="width: 250px; height: 250px"
                  loop
                  autoplay
                ></lottie-player>
              </v-container>
            </v-col>
            <v-col cols="12" sm="6">
              <v-form ref="form" v-model="valid" :lazy-validation="lazy">
                <v-text-field
                  v-model="name"
                  :counter="20"
                  :rules="nameRules"
                  label="Ad Soyad"
                  required
                ></v-text-field>

                <v-text-field
                  v-model="email"
                  :rules="emailRules"
                  label="E-mail"
                  required
                ></v-text-field>

                <v-text-field
                  v-model="telephone"
                  :rules="telephoneRules"
                  label="Telefon"
                  required
                ></v-text-field>

                <v-menu
                  ref="menu"
                  v-model="entryMenu"
                  :close-on-content-click="false"
                  transition="scale-transition"
                  offset-y
                  min-width="290px"
                >
                  <template v-slot:activator="{ on, attrs }">
                    <v-text-field
                      v-model="entryDate"
                      label="Giriş Tarihi"
                      prepend-icon="mdi-calendar"
                      readonly
                      v-bind="attrs"
                      v-on="on"
                    ></v-text-field>
                  </template>
                  <v-date-picker
                    ref="picker"
                    v-model="entryDate"
                    :min="new Date().toISOString().substr(0, 10)"
                    max="2025-01-01"
                    @change="saveEntry"
                  ></v-date-picker>
                </v-menu>
                <!--  -->
                <v-menu
                  v-if="entryDate != null"
                  ref="menu"
                  v-model="exitMenu"
                  :close-on-content-click="false"
                  transition="scale-transition"
                  offset-y
                  min-width="290px"
                >
                  <template v-slot:activator="{ on, attrs }">
                    <v-text-field
                      v-model="exitDate"
                      label="Çıkış Tarihi"
                      prepend-icon="mdi-calendar"
                      readonly
                      v-bind="attrs"
                      v-on="on"
                    ></v-text-field>
                  </template>
                  <v-date-picker
                    ref="picker"
                    v-model="exitDate"
                    :min="entryDate"
                    max="2025-01-01"
                    @change="saveExit"
                  ></v-date-picker>
                </v-menu>

                <v-btn
                  v-if="exitDate != null"
                  :disabled="!valid"
                  color="primary"
                  :dark="valid"
                  rounded
                  block
                  class="mt-3"
                >
                  Gönder
                </v-btn>
              </v-form>
              <v-container fluid>
                <v-row align="center" justify="center">
                  <v-col>
                    <h1 class="font-weight-light display-1">Konumumuz</h1>
                    <br />
                    <v-row>
                      <v-col>
                        <lottie-player
                          class="mx-auto"
                          src="https://assets7.lottiefiles.com/packages/lf20_v3WrCt.json"
                          background="transparent"
                          speed="1"
                          style="width: 150px; height: 150px"
                          loop
                          autoplay
                        ></lottie-player>
                      </v-col>
                      <v-col>
                        <v-card
                          class="mx-auto"
                          shaped
                          elevation="5"
                          max-height="280"
                          max-width="280"
                        >
                          <iframe
                            src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d820130.1466586638!2d-117.33246903668795!3d36.587051600912346!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x80c739a21e8fffb1%3A0x1c897383d723dd25!2sDeath%20Valley%2C%20Kaliforniya%2C%20Amerika%20Birle%C5%9Fik%20Devletleri!5e0!3m2!1str!2str!4v1604183976175!5m2!1str!2str"
                            width="280"
                            height="280"
                            frameborder="0"
                            style="border: 0"
                            allowfullscreen=""
                            aria-hidden="false"
                            tabindex="0"
                          ></iframe>
                        </v-card>
                      </v-col>
                    </v-row>
                  </v-col>
                </v-row>
              </v-container>
            </v-col>
          </v-row>
        </v-col>
      </v-row>
    </v-container>
    <div class="svg-border-waves text-white">
      <v-img src="~@/assets/img/borderWavesBlue.svg" />
    </div>
  </section>
</template>

<style scoped>
#contact {
  background-color: #f4f7f5;
}

.svg-border-waves .v-image {
  position: absolute;
  bottom: 0;
  left: 0;
  height: 3rem;
  width: 100%;
  overflow: hidden;
}
</style>

<script>
export default {
  data: () => ({
    valid: true,
    entryDate: null,
    exitDate: null,
    entryMenu: false,
    exitMenu: false,
    name: "",
    nameRules: [
      (v) => !!v || "Ad-Soyad boş bırakılamaz.",
      (v) => (v && v.length >= 3) || "Minimum 3 karakter girmelisiniz",
    ],
    email: "",
    emailRules: [
      (v) => !!v || "E-mail boş bırakılamaz.",
      (v) => /.+@.+\..+/.test(v) || "Geçerli bir e-posta adresi giriniz.",
    ],
    telephone: "",
    telephoneRules: [
      (v) => !!v || "Telefon numarası boş bırakılamaz.",
      (v) =>
        /(05|5)[0-9][0-9][1-9]([0-9]){6}/.test(v) ||
        "Geçerli bir telefon numarası giriniz.",
    ],
    lazy: false,
  }),
  watch: {
    entryMenu(val) {
      val && setTimeout(() => (this.$refs.picker.activePicker = "YEAR"));
    },
    exitMenu(val) {
      val && setTimeout(() => (this.$refs.picker.activePicker = "YEAR"));
    },
  },
  methods: {
    saveEntry(entryDate) {
      this.$refs.menu.save(entryDate);
    },
    saveExit(exitDate) {
      this.$refs.menu.save(exitDate);
    },
  },
};
</script>
