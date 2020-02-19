<template>
  <v-container>
    <v-layout text-center wrap>
      <v-img :src="image" contain height="200"></v-img>
      <div>{{ vehicleData }}</div>
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
  data () {
      return {
          vehicleData: null
      }
  },
  computed: {
      imageUrl () {
        return '../..' + this.details.media[0].url
      }
  },
  mounted() {
    axios.get(`http://localhost:3000/${this.details.id}`).then(({ data }) => {
      this.vehicleData = data;
    });
  }
};
</script>