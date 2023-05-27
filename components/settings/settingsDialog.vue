<script setup>
import defaultSettings from "./defaultSettings.json";

const props = defineProps(["modelValue"]);
const emit = defineEmits(["update:modelValue", "close"]);

const dialog = computed({
  get() {
    return props.modelValue;
  },
  set(newValue) {
    emit("update:modelValue", newValue);
  },
});

const settingsTab = ref("Villains");
const settingsTabItems = ref([
  { title: "Villains", value: "Villains" },
  { title: "Env", value: "Env" },
  { title: "Heroes", value: "Heroes" },
  { title: "Sets", value: "Sets" },
  { title: "Settings", value: "Settings" },
]);
const settings = ref(defaultSettings);

const save = () => {
  emit("close");
  localStorage.setItem("settings", JSON.stringify(settings));
};
</script>

<template>
  <v-card>
    <v-card-title class="pa-0 ma-0">
      <v-toolbar dark color="primary" flat>
        <v-toolbar-title>Settings</v-toolbar-title>
        <v-spacer></v-spacer>
        <v-toolbar-items>
          <v-btn variant="text" @click="save"> Save </v-btn>
        </v-toolbar-items>
        <template v-slot:extension>
          <v-tabs v-model="settingsTab" bg-color="primary" class="text-no-wrap">
            <v-tab
              v-for="item in settingsTabItems"
              :key="item.value"
              :value="item.value"
            >
              {{ item.title }}
            </v-tab>
          </v-tabs>
        </template>
      </v-toolbar>
    </v-card-title>
    <v-card-text class="pa-0 ma-0">
      <v-window v-model="settingsTab">
        <v-window-item
          :value="settingsTabItems[0].value"
          class="rounded-shaped bg-red-darken-2"
          ><SettingsVillains
        /></v-window-item>
        <v-window-item
          :value="settingsTabItems[1].value"
          class="rounded-shaped bg-purple-darken-2"
          ><SettingsHeroes
        /></v-window-item>
        <v-window-item
          :value="settingsTabItems[2].value"
          class="rounded-shaped bg-blue-darken-2"
          ><SettingsEnv
        /></v-window-item>
        <v-window-item :value="settingsTabItems[3].value" class="rounded-shaped"
          ><SettingsSets
        /></v-window-item>
        <v-window-item :value="settingsTabItems[4].value" class="rounded-shaped"
          ><Settings
        /></v-window-item>
      </v-window>
    </v-card-text>
  </v-card>
</template>