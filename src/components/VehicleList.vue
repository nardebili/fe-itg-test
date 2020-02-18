<template>
    <div>
        {{ vehicles }}
    </div>
</template>

<script>
import axios from "axios";
export default {
    name: 'VehicleList',
    data() {
        return {
            vehicles: {}
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