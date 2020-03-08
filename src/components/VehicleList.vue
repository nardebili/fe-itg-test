<template>
  <div>
    <div class="d-none d-xl-flex d-lg-flex wide-view">
      <v-card v-for="vehicle in vehicles" :key="vehicle.id" class="pa-2" outlined tile>
        <VehicleView :details="vehicle" :image="images[vehicle.id]" />
      </v-card>
    </div>
    <v-container class="d-xl-none d-lg-none grey lighten-5">
      <v-row no-gutters>
        <v-col
          v-for="vehicle in vehicles"
          :key="vehicle.id"
          cols="12"
          sm="3"
          xs="12"
          class="d-flex align-stretch"
        >
          <v-card class="pa-2" outlined tile>
            <VehicleView :details="vehicle" :image="images[vehicle.id]" />
          </v-card>
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<script>
import axios from "axios";
import VehicleView from "./VehicleView";
export default {
  name: "VehicleList",
  components: {
    VehicleView
  },
  data() {
    return {
      vehicles: {},
      images: {
        fpace: require("../../images/fpace_k17.jpg"),
        ftype: require("../../images/ftype_k17.jpg"),
        xf: require("../../images/xf_k17.jpg"),
        xe: require("../../images/xe_k17.jpg"),
        xj: require("../../images/xj_k16.jpg")
      }
    };
  },
  mounted() {
    axios.get("http://localhost:3000/vehicles").then(({ data }) => {
      this.vehicles = data;
    });
  }
};
</script>

<style lang="scss">
  .wide-view {
    max-width: 1600px;
    overflow-x: scroll;
  }
</style>