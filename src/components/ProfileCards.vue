<template>
         <v-flex auto style="padding:1%" >
  <v-card
    class="mx-auto"
    min-width="300"
    max-width="300"
  >
    <v-img
      :src="this.person.images.main"
      max-height="200px"
      contain
    ></v-img>

    <v-card-title>
      {{this.person.name.first}} {{this.person.name.middle}} {{this.person.name.last}} 
    </v-card-title>

    <v-card-subtitle>
     {{this.person.species}} - {{this.person.gender}} - {{this.person.age}}
    </v-card-subtitle>

    <v-card-actions>
      <v-btn
        color="orange lighten-2"
        text
      >
        Details
      </v-btn>

      <v-spacer></v-spacer>

      <v-btn
        icon
        @click="curShow = !curShow"
      >
        <v-icon>{{ curShow ? 'mdi-chevron-up' : 'mdi-chevron-down' }}</v-icon>
      </v-btn>
    </v-card-actions>

    <v-expand-transition>
      <div v-show="curShow">
        <v-divider></v-divider>

        <v-card-text>
            <ol>
                <li v-for="(sayings,index) in this.person.sayings" :key="index">{{sayings}}     
                    <v-btn
                    outlined
                    small
                    fab
                    color="indigo"
                    x-small
                    @click="editSayings(index)"
                    >
                        <v-icon x-small>mdi-pencil</v-icon>
                    </v-btn>
                </li>
        </ol>
        </v-card-text>
      </div>
    </v-expand-transition>
  </v-card>
          <DrawerSample v-model="drawer" :textData="sayingData" :postion="indx" @saveSaying="updateSaying"/>
       </v-flex>
       
</template>

<script>
import DrawerSample from './DrawerSample.vue';
export default {

    props:["person"],
    components:
    {
        DrawerSample
    },
    data: function()
    {
        return {
            curShow: this.person.Active,
            drawer: false,
            sayingData: "",
            indx:0
        }
    },
    methods:{
        editSayings:function(index)
        {
            this.sayingData = this.person.sayings[index];
            this.indx = index;
            this.drawer = true;
        },
        updateSaying:function(item)
        {
            this.drawer = false;
            item.personid = this.person.id
            this.$emit("editSayings",item)
            console.log(item)
        }
    }

}
</script>

<style>

</style>