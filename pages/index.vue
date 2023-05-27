<template>
  <v-container>
    <v-dialog
      v-model="dialog"
      fullscreen
      scrollable
      :scrim="false"
      transition="dialog-bottom-transition"
    >
      <template />
      <SettingsDialog @close="dialog = false"></SettingsDialog>
    </v-dialog>
    <v-row>
      <v-col>
        <v-card class="bg-blue-lighten-5">
          <headerTitle v-model="dialog" :inactiveGame="inactiveGame" />
          <hCount v-model="H" />
        </v-card>
        <h3>{{ H }}</h3>
      </v-col>
    </v-row>
  </v-container>
</template>
  
<script setup>
const gameSetup = ref({
  heroes: [],
  villain: "",
  env: "",
  advanced: false,
  event: false,
});
const dialog = ref(false);
const H = ref("3");

const inactiveGame = computed(() => {
  return gameSetup.value.villain == "";
});
</script>
  