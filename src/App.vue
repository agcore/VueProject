<template>
  <v-app>
    <!-- <v-main>
      <HelloWorld v-model="drawer1" />
      <DrawerSample v-model="drawer2"/>
      <v-btn @click="drawer1 = !drawer1"> Drawer 1 </v-btn>
      <v-btn @click="drawer2 = !drawer2"> Drawer 2 </v-btn>
    </v-main> -->


<div>

          <v-app-bar color="deep-purple" dark>
            <v-app-bar-nav-icon @click="drawer = true"></v-app-bar-nav-icon>
             <v-toolbar-title>Title</v-toolbar-title>
          </v-app-bar>
          <v-navigation-drawer v-model="drawer" absolute temporary>
            <v-list nav dense>
              <v-list-item-group v-model="group" active-class="deep-purple--text text--accent-4">
                <v-list-item>
                  <v-list-item-icon>
                    <v-icon>mdi-home</v-icon>
                  </v-list-item-icon>
                  <v-list-item-title>Home</v-list-item-title>
                </v-list-item>
<v-list-item>
                  <v-list-item-icon>
                    <v-icon>mdi-account</v-icon>
                  </v-list-item-icon>
                  <v-list-item-title>Account</v-list-item-title>
                </v-list-item>
              </v-list-item-group>
            </v-list>
          </v-navigation-drawer>
                <HelloWorld v-model="drawer1" />
      <DrawerSample v-model="drawer2"/>
      <v-btn @click="drawer1 = !drawer1"> Drawer 1 </v-btn>
      <v-btn @click="drawer2 = !drawer2"> Drawer 2 </v-btn>
</div>



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
        drawer:false,
        drawer1:false,
        drawer2:false,
        group: null
      }
  },

  components: {
    HelloWorld,
    DrawerSample
  },
};
</script>
