<template>
  <q-page class="flex flex-center">
    <q-input
      outlined
      bottom-slots
      v-model="text"
      label="Label"
      counter
      maxlength="12"
      :dense="dense"
    >
      <template v-slot:before>
        <q-icon name="flight_takeoff" />
      </template>

      <template v-slot:append>
        <q-icon
          v-if="text !== ''"
          name="close"
          @click="text = ''"
          class="cursor-pointer"
        />
        <q-icon name="search" />
      </template>

      <template v-slot:hint> Field hint </template>
    </q-input>
  </q-page>
</template>

<script>
import { defineComponent } from "vue";

export default defineComponent({
  name: "IndexPage",
});
</script>
