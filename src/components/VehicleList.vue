<template>
  <v-container class="grey lighten-5">
    <v-row no-gutters>
      <v-col
        v-for="vehicle in vehicles"
        :key="vehicle.id"
        cols="12"
        sm="3"
      >
        <v-card
          class="pa-2"
          outlined
          tile
        >
          <VehicleView :details="vehicle" :image="images[vehicle.id]" />
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import axios from "axios";
import VehicleView from './VehicleView'
export default {
    name: 'VehicleList',
    components: {
        VehicleView
    },
    data() {
        return {
            vehicles: {},
            images: {
                fpace: require('../../images/fpace_k17.jpg'),
                ftype: require('../../images/ftype_k17.jpg'),
                xf: require('../../images/xf_k17.jpg'),
                xe: require('../../images/xe_k17.jpg'),
                xj: require('../../images/xj_k16.jpg')
            }
        }
    },
    mounted() {
      axios
        .get(
          "http://localhost:3000/vehicles"
        ).then(({data}) => {
            this.vehicles = data
        })
    }
}
</script>