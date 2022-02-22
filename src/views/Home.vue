<template>
  <div>
    <Toolbar/>
    <v-row align="center" justify="center" style="padding-top: 150px;">
      <v-card class="box elevation-24" style="border-radius: 30px;">
        <StreamBarcodeReader
            style="margin-bottom: 5px"
            @decode="onDecode"
            @loaded="onLoaded"
        ></StreamBarcodeReader>

      </v-card>
    </v-row>
    <v-row style="height: 50px" justify="center" align="center">
      <h2>
        scanner
      </h2>
    </v-row>
    <v-col cols="auto">
      <v-dialog
          transition="dialog-top-transition"
          max-width="600"

          v-model="dialog"
      >

        <template v-slot:default="dialog">
          <v-card height="300">
            <v-toolbar
                class="toolbar-color"
                dark
            >
              <v-img src="@/assets/img/logo_qr.png" max-width="30px"/>

              <h3>
                Response
              </h3>
            </v-toolbar>
            <v-row style="padding-top: 80px" align="center" justify="center">
              <h3>Decode Qr code : {{ qrcode }}</h3>
            </v-row>
            <v-row style="padding-top: 40px" align="center" justify="center">
              <h3>Response Web Service : {{ result }}</h3>
            </v-row>

            <v-card-actions style="padding-top: 50px" class="justify-end">
              <v-btn
                  @click="dialog.value = false"
                  color="#C01A1A"
              >
                <h3>
                  Close
                </h3>
              </v-btn>
            </v-card-actions>
          </v-card>
        </template>
      </v-dialog>
    </v-col>
    <v-snackbar
        v-model="errorMassage"
    >
      <v-row justify="center" align="center">
        <h3>
          {{ textError }}
        </h3>
      </v-row>
    </v-snackbar>

  </div>

</template>

<script>
import Toolbar from '../components/Header.vue'
import {StreamBarcodeReader} from "vue-barcode-reader";


export default {
  data() {
    return {
      dialog: false,
      result: undefined,
      errorMassage: false,
      qrcode: undefined,
      textError: "Error Web Service"

    }
  },
  components: {
    Toolbar,
    StreamBarcodeReader,
  },

  methods: {
//======================================================================================
    onDecode(decodeQr) {
      console.log(`Decode Qr code${decodeQr}`)
      this.qrcode = decodeQr
      this.sendQr(decodeQr)
    },
//======================================================================================
    //log start
    onLoaded() {
      console.log(`Ready to start scanning qr codes`)
    },
//======================================================================================
    sendQr(value) {
      this.axios.post("https://www.evara.life:3086/list_test", {
        qr: value.toString()
      }).then(response => {
            this.result = response.data
            this.dialog = true
          }
      ).catch(() => {
            this.errorMassage = true
          }
      );
    }
//======================================================================================
  }
}
</script>
<style>
.toolbar-color {
  background: linear-gradient(
      195deg, rgb(66, 66, 74), rgb(25, 25, 25));
}
</style>