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
            label="Outlined"
            outlined
          ></v-text-field>
          </v-list-item>

          <v-list-item>
            <v-list-item-title>Bar</v-list-item-title>
          </v-list-item>

          <v-list-item>
            <v-list-item-title>Fizz</v-list-item-title>
          </v-list-item>

          <v-list-item>
            <v-list-item-title>Buzz</v-list-item-title>
          </v-list-item>

      </v-list>

    </v-navigation-drawer>
</template>

<script>
  export default {
    name: 'HelloWorld',
    props : ["drawer"],
        model: {
        prop: 'drawer',
        event: 'drawerChange'
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
  }
}
  }
</script>
