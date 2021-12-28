<template>
  <v-app>
    <v-main>
      <HelloWorld v-model="drawer1" />
      <DrawerSample v-model="drawer2"/>
      <v-btn @click="drawer1 = !drawer1"> Drawer 1 </v-btn>
      <v-btn @click="drawer2 = !drawer2"> Drawer 2 </v-btn>
    </v-main>
  </v-app>
</template>

<script>
import HelloWorld from './components/HelloWorld';
import DrawerSample from './components/DrawerSample';

export default {
  name: 'App',
  data: function()
  {
      return{
        drawer1:false,
        drawer2:false
      }
  },

  components: {
    HelloWorld,
    DrawerSample
  },
};
</script>
