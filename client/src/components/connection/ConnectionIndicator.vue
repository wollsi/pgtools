<template>
  <div>
    <v-chip
      class="ma-1"
      :color="numberActiveConnections > 0 ? 'green' : 'red'"
      text-color="white"
      label
    >
      Connections
      <v-avatar
        right
        :class="numberActiveConnections > 0 ? 'green darken-4' : 'red darken-4'"
      >
        {{numberActiveConnections}}
      </v-avatar>
    </v-chip>

    <v-chip
      class="ma-1"
      :color="$store.getters.websocketStatus > 0 ? 'green' : 'red'"
      text-color="white"
      label
    >
      Backend
      <v-avatar
        right
        :class="$store.getters.websocketStatus > 0 ? 'green darken-4' : 'red darken-4'"
      >
        <v-icon>{{$store.getters.websocketStatus > 0 ? 'mdi-server-plus' : 'mdi-server-minus'}}</v-icon>
      </v-avatar>
    </v-chip>
  </div>
</template>

<script>
export default {
  name: 'ConnectionIndicator',
  data: function () {
    return {}
  },
  computed: {
    numberActiveConnections() {
      return this.$store.getters.activeConnections.length;
    }
  },
  methods: {
    gotoConnections() {
      if (this.$route.path !== '/connections') {
        this.$router.push('connections');
      }
    },
    getColor() {
      if (this.$store.getters.websocketStatus) return "green";
      else return 'red';
    }
  }
}
</script>


<style scoped>
</style>