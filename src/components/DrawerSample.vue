<template>
      <v-navigation-drawer
      v-model="curDrawer"
      absolute
      bottom
      temporary
      right
      width="25%"
    >
  <v-list
        
        dense
      >
          <v-list-item>
                      <v-text-field
            label="Saying"
            outlined
            v-model="sayingText"
          ></v-text-field>
          </v-list-item>
          <v-list-item>
            <v-btn block dark @click="saveSaying">Save</v-btn>
          </v-list-item>
      </v-list>

    </v-navigation-drawer>
</template>



<script>
export default {
name: "DrawerSample",
props : ["drawer","textData","postion"],
model: {
  prop:'drawer',
  event: 'drawerChange'
},
data: function()
{
  return{
    editedSaying:""
  }
},

computed : {
  curDrawer : {
    get: function()
    {
      return this.drawer
    },
    set : function(value)
    {
      this.$emit('drawerChange',value);
    }
  },
  sayingText : {
    get: function(){
      if (this.editedSaying)
      {
        return this.editedSaying
      }
      else{
        return this.textData
      }
    },
    set:function(newVal)
    {
      this.editedSaying = newVal
    }
  }
},
methods:{
  saveSaying: function()
  {
    this.$emit('saveSaying',{
      data :this.sayingText,
      index: this.postion
    })
    this.sayingText = ""
  }
}

}
</script>

<style>

</style>