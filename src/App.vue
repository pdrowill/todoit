<template>
  <v-app>
    <v-app-bar
      app
      color="deep-purple darken-1"
      dark
    >
      <v-toolbar-title>ToDoit</v-toolbar-title>

      <v-spacer></v-spacer>
      
      <v-btn text to="/"><span class="mr-2">Home</span></v-btn>
      <v-btn text to="/About"><span class="mr-2">About</span></v-btn>
      <v-btn
        href="https://vuetifyjs.com/en/components/app-bars/#app-bars"
        target="_blank"
        text
      >
        <span class="mr-2">Doc</span>
        <v-icon>mdi-open-in-new</v-icon>
      </v-btn>
    </v-app-bar>
    

    <v-main> 
      <router-view></router-view>
    </v-main>
  </v-app>
</template>

<script>

export default {
  name: 'App',
  
  components: {
    
  },

  data() {
    return {
      tasks: [
        { title: 'Read a comic', subtitle: 'Alan Moore comic', pending: true},
        { title: 'Read a comic', subtitle: 'Alan Moore comic', pending: true},
        { title: 'Get another comic', subtitle: 'This time, a Jeff Lemire one.', pending: true}
      ]
    }
  },
};
</script>
