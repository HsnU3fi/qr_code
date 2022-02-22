<template >
  <v-app>
    <router-view/>
  </v-app>
</template>

<style>
@font-face {
  font-family: IranSans;
  src: url('/assets/fonts/iransans/IRANSansWeb_Light.eot');
  src: url('/assets/fonts/iransans/IRANSansWeb_Light.eot?#iefix') format('embedded-opentype'),
  url('assets/fonts/iransans/IRANSansWeb_Light.woff2') format('woff2'),
  url('assets/fonts/iransans/IRANSansWeb_Light.woff') format('woff'),
  url('assets/fonts/iransans/IRANSansWeb_Light.ttf') format('truetype');
  font-weight: normal;
}

* {
  font-family: 'IranSans', sans-serif;
  font-size: 15px;
  overflow: hidden;
}

</style>
