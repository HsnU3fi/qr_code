<template>
  <div>
    <v-app-bar class="appbar" dark dense height="80" app>
            <v-img src="@/assets/img/logo_qr.png" max-width="50px"/>
      <v-toolbar-title  class="toolbar">
        QR Code Reader
      </v-toolbar-title>
      <v-spacer></v-spacer>
    </v-app-bar>
  </div>
</template>



<style>
.toolbar {
  color: white;font-weight:900;font-size: 22px;
  margin-left: 5px;
}
.appbar {
  background: linear-gradient(
  195deg, rgb(66, 66, 74), rgb(25, 25, 25));
}
</style>
