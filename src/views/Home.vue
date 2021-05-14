<template>
  <main v-if="!loading">
    <DataTitle :text="title" :dataDate="dataDate" />

    <DataBoxes :stats="stats" />
  </main>
  <main class="flex flex-col align-center justify-center text-center" v-else>
    <div class="text-gray-500 text-3xl mt-10 mb-6">
      Fetching data
    </div>
    <img :src="loadingImage" class="w-24 m-auto" alt="" />
  </main>
</template>

<script>
import DataTitle from '@/components/DataTitle'
import DataBoxes from '@/components/DataBoxes'

export default {
  name: "Home",
  components: {
    DataTitle,
    DataBoxes
  },
  data() {
    return {
      loading: true,
      title: "Sri Lanka",
      dataDate: "",
      stats: {},
      hospitals: [],
      loadingImage: require("../assets/hourglass.gif"),
    };
  },
  methods: {
    async fetchCovidData() {
      const res = await fetch(
        "https://www.hpb.health.gov.lk/api/get-current-statistical"
      );
      const data = await res.json();
      return data;
    },
  },
  async created() {
    const data = await this.fetchCovidData();

    this.dataDate = data.data.update_date_time;
    this.stats = data.data;
    this.hospitals = data.data.hospital_data;
    this.loading = false;
  },
};
</script>
