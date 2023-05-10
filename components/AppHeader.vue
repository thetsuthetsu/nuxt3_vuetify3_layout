<template>
  <v-app-bar color="primary" prominent>
    <v-app-bar-nav-icon
      variant="text"
      @click.stop="drawer = !drawer"
    ></v-app-bar-nav-icon>
    <v-toolbar-title>Composition API Samples</v-toolbar-title>
    <v-spacer></v-spacer>
    <v-btn variant="text" icon="mdi-magnify"></v-btn>
    <v-btn variant="text" icon="mdi-filter"></v-btn>
    <v-btn variant="text" icon="mdi-dots-vertical"></v-btn>
  </v-app-bar>
  <v-navigation-drawer
    v-model="drawer"
    :rail="rail"
    width="300"
    permanent
    @click="rail = false"
  >
    <v-list-item prepend-icon="mdi-home" title="Home" to="/">
      <template v-slot:append>
        <v-btn
          variant="text"
          icon="mdi-chevron-left"
          @click.stop="rail = !rail"
        ></v-btn>
      </template>
    </v-list-item>
    <v-divider></v-divider>
    <v-list v-model:opened="open" nav>
      <v-list-group value="Composition API">
        <template v-slot:activator="{ props }">
          <v-list-item
            v-bind="props"
            prepend-icon="mdi-video-input-component"
            title="Composition API"
          ></v-list-item>
        </template>
        <v-list-group value="Reactives">
          <template v-slot:activator="{ props }">
            <v-list-item v-bind="props" title="Reactives"></v-list-item>
          </template>
          <v-list-item
            v-for="([title, icon, to], i) in reactives"
            :key="i"
            :title="title"
            :prepend-icon="icon"
            :value="title"
            :to="to"
          ></v-list-item>
        </v-list-group>
        <v-list-group value="LifeCycleHooks">
          <template v-slot:activator="{ props }">
            <v-list-item v-bind="props" title="LifeCycleHooks"></v-list-item>
          </template>
          <v-list-item
            v-for="([title, icon], i) in lifecyclehooks"
            :key="i"
            :value="title"
            :title="title"
            :prepend-icon="icon"
          ></v-list-item>
        </v-list-group>
        <v-list-group value="Injections">
          <template v-slot:activator="{ props }">
            <v-list-item v-bind="props" title="Injections"></v-list-item>
          </template>
          <v-list-item
            v-for="([title, icon], i) in injections"
            :key="i"
            :value="title"
            :title="title"
            :prepend-icon="icon"
          ></v-list-item>
        </v-list-group>
      </v-list-group>
    </v-list>
  </v-navigation-drawer>
</template>
<script setup>
import { ref } from "vue";
const drawer = ref(true);
const rail = ref(true);
const open = ref(["Composition API"]);
const reactives = ref([
  ["ReactiveArrays", "mdi-view-array", "/reactives/arrays"],
]);
const lifecyclehooks = ref([
  ["onMounted", "mdi-plus-outline"],
  ["onUpdated", "mdi-update"],
]);
const injections = ref([
  ["provide", "mdi-tag-plus"],
  ["inject", "mdi-needle"],
]);
</script>
