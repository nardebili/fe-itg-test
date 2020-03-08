<template>
  <v-app>
    <v-app-bar
      app
      color="primary"
      dark
    >
      ITG Test
    </v-app-bar>

    <v-content>
      <VehicleList/>
    </v-content>
  </v-app>
</template>

<script>
// import HelloWorld from './components/HelloWorld';
import VehicleList from './components/VehicleList';

export default {
  name: 'App',

  components: {
    // HelloWorld,
    VehicleList
  },

  data: () => ({
    //
  }),
};
</script>
