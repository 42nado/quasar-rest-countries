<template>
  <q-page class="row justify-around">
    <div>
      <q-input
        class="search"
        outlined
        bottom-slots
        v-model="text"
        label="Search Country"
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
      </q-input>
    </div>
    <div class="q-pa-md filter">
      <q-btn-dropdown color="primary" label="Filter By Region">
        <q-list>
          <q-item clickable v-close-popup @click="onItemClick">
            <q-item-section>
              <q-item-label>Africa</q-item-label>
            </q-item-section>
          </q-item>

          <q-item clickable v-close-popup @click="onItemClick">
            <q-item-section>
              <q-item-label>America</q-item-label>
            </q-item-section>
          </q-item>

          <q-item clickable v-close-popup @click="onItemClick">
            <q-item-section>
              <q-item-label>Asia</q-item-label>
            </q-item-section>
          </q-item>
          <q-item clickable v-close-popup @click="onItemClick">
            <q-item-section>
              <q-item-label>Europe</q-item-label>
            </q-item-section>
          </q-item>
          <q-item clickable v-close-popup @click="onItemClick">
            <q-item-section>
              <q-item-label>Oceania</q-item-label>
            </q-item-section>
          </q-item>
        </q-list>
      </q-btn-dropdown>
    </div>
    <div class="country"></div>
  </q-page>
</template>

<script>
import { defineComponent } from "vue";

export default defineComponent({
  name: "IndexPage",
});
</script>

<style>
.q-page {
  padding-top: 15px;
}
</style>
