<template >
  <div>
    <v-app-bar color="purple darken-4" dark app dense>
      <v-toolbar-title>Ola</v-toolbar-title>
      <v-spacer></v-spacer>
      <v-toolbar-items class="hidden-sm-and-down">
        <v-btn
          v-for="(route, index) in scrollTags"
          :key="index"
          :to="route.to"
          class="text-capitalize"
          text
        >{{route.name}}</v-btn>
      </v-toolbar-items>
      <v-spacer></v-spacer>
      <v-btn
        v-for="(route,index) in buttons"
        :key="index"
        :to="route.to"
        class="text-capitalize hidden-sm-and-down"
        text
      >{{route.name}}</v-btn>
      <v-app-bar-nav-icon @click="openCloseSideBar = !openCloseSideBar" class="hidden-md-and-up"></v-app-bar-nav-icon>
    </v-app-bar>
    <SideBarLinks :open="openCloseSideBar" :routes="routes"></SideBarLinks>
  </div>
</template>

<script>
import SideBarLinks from "./SideBarLinks.vue";

export default {
  name: "NavBar",
  data() {
    return {
      openCloseSideBar: false,
      routes: [
        { name: "que es", to: "", icon: "mdi-help-box" },
        { name: "porque", to: "", icon: "mdi-gesture" },
        { name: "funciones", to: "", icon: "mdi-shape-plus" },
        { name: "sobre mi", to: "", icon: "mdi-information-outline" },
        { name: "log in", to: "/login", icon: "mdi-login" },
        { name: "sign up", to: "/sign-up", icon: "mdi-account-plus-outline" }
      ]
    };
  },
  computed: {
    scrollTags: function() {
      return this.routes.filter((i, index) => index < this.routes.length - 2);
    },
    buttons: function() {
      return this.routes.filter((i, index) => index > this.routes.length - 3);
    }
  },
  components: {
    SideBarLinks
  }
};
</script>
