<template>
  <v-app>
    <v-app-bar
      app
      color="primary"
      dark
    >
      <div class="d-flex align-center">
        <h1>Kanby: your awesome personal dashboard</h1>
      </div>

      <v-spacer></v-spacer>

    </v-app-bar>

    <v-main>
      <v-container fluid>
        <KanbanDashboard />
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
import KanbanDashboard from './components/KanbanDashboard';

export default {
  name: 'App',

  components: {
    KanbanDashboard,
  },

  data: () => ({
    //
  }),
};
</script>
<style>
  @import '../public/styles.css';
</style>
