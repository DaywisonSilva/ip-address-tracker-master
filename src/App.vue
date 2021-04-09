<template>
  <div>
    <div class="background__app">
      <h1 class="title-background__app">IP Address Tracker</h1>
      <app-input
        @click="reqAPI()"
        @keyup.enter="reqAPI()"
        @input="ip = $event.target.value"
        :ip="ip"
      />
      <card-info
        :ip="ip"
        :location="location"
        :timezone="timezone"
        :isp="isp"
      />
    </div>
    <l-map
      v-if="showMap"
      :zoom="zoom"
      :center="place"
      :options="mapOptions"
      style="height: calc(100vh - 260px); z-index: 1;"
      @update:center="centerUpdate"
      @update:zoom="zoomUpdate"
    >
      <l-tile-layer :url="url" />
      <l-marker :lat-lng="place" />
    </l-map>
  </div>
</template>

<script>
import { latLng } from "leaflet";
export default {
  data() {
    return {
      zoom: 15,
      url: "https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png",
      place: latLng(47.41322, -1.219482),
      currentZoom: 11.5,
      mapOptions: {
        zoomSnap: 0.5,
      },
      showMap: true,
      ip: "192.212.174.101",
      location: "",
      timezone: "",
      isp: "",
    };
  },
  components: {
    appInput: () => import("@/components/Input.vue"),
    cardInfo: () => import("@/components/CardInfo.vue"),
  },
  mounted() {
    fetch(
      `https://geo.ipify.org/api/v1?apiKey=at_y4t75ky3xvza1RV7CEWsa9XxinVDn&ipAddress=192.212.174.101`
    )
      .then((res) => res.json())
      .then((res) => {
        this.place = latLng(res.location.lat, res.location.lng);
        this.location = `${res.location.city}, ${res.location.country}, ${res.location.postalCode}`;
        this.timezone = `${res.location.timezone}`;
        this.isp = `${res.isp}`;
      });
  },
  methods: {
    zoomUpdate(zoom) {
      this.currentZoom = zoom;
    },
    centerUpdate(center) {
      this.currentCenter = center;
    },
    showLongText() {
      this.showParagraph = !this.showParagraph;
    },
    innerClick() {
      alert("Click!");
    },
    reqAPI() {
      fetch(
        `https://geo.ipify.org/api/v1?apiKey=at_y4t75ky3xvza1RV7CEWsa9XxinVDn&ipAddress=${this.ip}`
      )
        .then((res) => res.json())
        .then((res) => {
          this.place = latLng(res.location.lat, res.location.lng);
          this.location = `${res.location.city}, ${res.location.country}, ${res.location.postalCode}`;
          this.timezone = `${res.location.timezone}`;
          this.isp = `${res.isp}`;
        });
    },
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Roboto:wght@300;400;500;700&display=swap");
body {
  font-family: "Roboto", sans-serif;
  margin: 0;
  padding: 0;
}

h1,
h2,
h3,
h4,
h5,
h6 {
  padding: 0;
  margin: 0;
}

.background__app {
  width: 100%;
  height: 260px;
  position: relative;
  background-image: url("assets/images/pattern-bg.png");
  background-size: cover;
  background-position: center;
  display: grid;
  place-content: center;
  padding-bottom: 90px;
  box-sizing: border-box;
}

.title-background__app {
  color: white;
  font-weight: 500;
  text-align: center;
}
</style>
