
<template>

  <v-container fill-height fluid>
    <v-row
    class="flex-nowrap"
    >

  <v-flex d-flex>
   <v-layout wrap auto >
       <ProfileCards v-for="person in apiData"
        :key="person.id" 
        :person="person"
        @editSayings="updateSayings"
        @removeProfile="deleteProfile"
        @removeSaying="deleteSaying"
        />

   </v-layout>
</v-flex>
  


    </v-row>
        <!-- <HelloWorld v-model="drawer1" />
        <DrawerSample v-model="drawer2"/>
        <v-btn @click="drawer1 = !drawer1"> Drawer 1 </v-btn>
        <v-btn @click="drawer2 = !drawer2"> Drawer 2 </v-btn> -->
</v-container>

</template>

<script>
import HelloWorld from './HelloWorld';
import DrawerSample from './DrawerSample.vue';
import ProfileCards from './ProfileCards.vue';
import axios from 'axios'

export default {
name:"Container",
  components: {
    HelloWorld,
    DrawerSample,
    ProfileCards
  },
  data: function()
  {
      return {
      drawer1: false,
      drawer2:false,
      apiData: null,
      showData: false
      }
  },
  mounted: function ()
  {
        axios.get('https://api.sampleapis.com/futurama/characters').then((response) => {
                   this.apiData= response.data
                   this.apiData.forEach(element => {
                       element.Active = false;
                   });
                    console.log(this.apiData)
        })

  },
  methods: {
      showBotton:function (person)
      {
          var foundIndex = this.apiData.findIndex(x => x.id == person.id);
            this.apiData[foundIndex].Active = !this.apiData[foundIndex].Active;
      },
      updateSayings: function (item)
      {
          var foundIndex = this.apiData.findIndex(x => x.id == item.personid);
          this.apiData[foundIndex].sayings[item.index] = item.data
      },
      deleteProfile:function(index)
      {
        this.apiData = this.apiData.filter(function( obj ) {
          return obj.id !== index;
        });
      },
      deleteSaying: function(data){
         var foundIndex = this.apiData.findIndex(x => x.id == data.id);
        this.apiData[foundIndex].sayings.splice(data.index,1)
      }
  }
}
</script>

<style>

</style>