<script setup>
const props = defineProps(["modelValue"]);
const emit = defineEmits(["update:modelValue"]);

const H = computed({
  get() {
    return props.modelValue;
  },
  set(newValue) {
    emit("update:modelValue", newValue);
  },
});
</script>

<template>
  <div class="d-flex align-center flex-column">
    Hero Count:
    <v-btn-toggle
      v-model="H"
      divided
      size="small"
      color="deep-purple-accent-3"
      density="compact"
    >
      <v-btn size="small" value="3">3</v-btn>
      <v-btn size="small" value="4">4</v-btn>
      <v-btn size="small" value="5">5</v-btn>
      <v-btn size="small" value="?">?</v-btn>
    </v-btn-toggle>
  </div>
</template>