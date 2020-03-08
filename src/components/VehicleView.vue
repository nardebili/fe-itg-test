<template>
  <v-container>
    <v-layout text-center wrap>
      <v-img :src="image" contain height="200" class="mb-md-n2"></v-img>
      <div d-flex justify-center class="mx-6 mt-lg-6">
        <div class="headline font-weight-black text-uppercase mb-6 mt-2 vehicle-name">{{vehicleData.id}}</div>
        <p class="text--secondary">{{ `From ${vehicleData.price}`}}</p>
        <p class="text--secondary">{{ vehicleData.description }}</p>
      </div>
    </v-layout>
  </v-container>
</template>

<script>
import axios from "axios";
export default {
  name: "VehicleView",
  props: {
    details: {
      type: Object,
      required: true
    },
    image: {
      type: String,
      required: true
    }
  },
  data() {
    return {
      vehicleData: null
    };
  },
  computed: {
    imageUrl() {
      return "../.." + this.details.media[0].url;
    }
  },
  mounted() {
    axios.get(`http://localhost:3000/${this.details.id}`).then(({ data }) => {
      this.vehicleData = data;
    });
  }
};
</script>

<style lang='scss'>
.vehicle-name {
  border-style: solid;
  border-width: medium 0px;
}
</style>