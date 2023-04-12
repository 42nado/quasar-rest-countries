<template>
  <q-page class="grid items-center">
    <h5>All Countries</h5>
    <div class="flex country-cards row justify-around">
      <q-card
        v-for="country in countries"
        :key="country.name.common"
        class="my-card"
      >
        <q-img :src="getCountryDetails(country).flag" />
        <q-card-section>
          <div class="text-h6">{{ getCountryDetails(country).name }}</div>
          <div class="text-subtitle2">
            Population: {{ getCountryDetails(country).population }}
          </div>
          <div class="text-subtitle2">
            Region: {{ getCountryDetails(country).region }}
          </div>
          <div class="text-subtitle2">
            Capital: {{ getCountryDetails(country).capital }}
          </div>
        </q-card-section>
      </q-card>
    </div>
  </q-page>
</template>

<script>
import { ref } from "vue";
import axios from "axios";

export default {
  setup() {
    let countries = ref([]);
    // create a function to fetch the data from the API and store it in the countries variable
    const fetchCountries = async () => {
      const response = await axios.get("https://restcountries.com/v3.1/all");
      countries.value = response.data;
      console.log(countries.value);
    };
    // call the function
    fetchCountries();

    // function to get the flag image and country name population, region and capital from the countries variable
    const getCountryDetails = (country) => {
      return {
        flag: country.flags.png,
        name: country.name.common,
        population: country.population,
        region: country.region,
        capital: country.capital,
      };
    };

    return { countries, getCountryDetails };
  },
};
</script>
<style lang="sass" scoped>
.my-card
  width: 200px
  max-width: 250px
  margin: 10px
</style>
