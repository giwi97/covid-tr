<template>
  <main v-if="!loading">
    <DataTitle :text="title" :dataDate="dataDate" />
    <div v-if="!hosClick">
      <DataBoxes :stats="stats" />
    </div>
    <div v-else>
      <HosData :stats="stats" />
    </div>
    <HospitalSelect @get-hospital="getHospitalData" :hospitals="hospitals" />
    <button @click="clearHospitalData" v-if="!stats.hospital_data"
      class="tw-bg-green-700 tw-text-white tw-rounded tw-p-3 tw-mt-10 focus:tw-outline-none hover:tw-bg-green-600"
    >
      Reset
    </button>
  </main>
  <main class="tw-flex tw-flex-col tw-align-center tw-justify-center tw-text-center" v-else>
    <div class="tw-text-gray-500 tw-text-3xl tw-mt-10 tw-mb-6">
      Fetching data
    </div>
    <img :src="loadingImage" class="tw-w-24 tw-m-auto" />
  </main>
</template>

<script>
import DataTitle from "@/components/DataTitle";
import DataBoxes from "@/components/DataBoxes";
import HospitalSelect from "@/components/HospitalSelect";
import HosData from "@/components/HosData";

export default {
  name: "Home",
  components: {
    DataTitle,
    DataBoxes,
    HospitalSelect,
    HosData,
  },
  data() {
    return {
      hosClick: false,
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
    getHospitalData(hospital) {
      this.stats = hospital;
      this.title = hospital.hospital.name;
      this.hosClick = true;
    },
    async clearHospitalData() {
      this.loading = true;
      const data = await this.fetchCovidData();
      this.title = 'Sri Lanka';
      this.stats = data.data;
      this.hosClick = false;
      this.loading = false;
    },
  },
  async created() {
    const data = await this.fetchCovidData();

    this.dataDate = data.data.update_date_time;
    this.stats = data.data;
    this.hospitals = data.data.hospital_data;
    this.loading = false;
    this.hosClick = false;
  },
};
</script>
