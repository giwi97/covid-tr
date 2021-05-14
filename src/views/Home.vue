<template>
  <div class="home">
    Hello World
  </div>
</template>

<script>
export default {
  name: "Home",
  components: {},
  data() {
    return {
      loading: true,
      title: 'data',
      dataDate: '',
      stats: {},
      countries: [],
      loadingImage: require('../assets/hourglass.gif')
    }
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
    
    this.dataDate = data.data.update_date_time
    this.stats = data.data
    this.countries = data.data.hospital_data
    this.loading = false
  },
};
</script>
