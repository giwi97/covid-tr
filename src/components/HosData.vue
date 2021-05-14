<template>
  <div class="shadow-md bg-blue-100 p-5 text-center rounded">
      <i class="fa fa-ambulance"></i>
      <h3 class="text-3xl text-blue-900 font-bold mb-4">
        Cases
      </h3>

      <div class="text-2xl mb-4">
        <span class="font-bold">
          Current Patients:
        </span>
        {{ numberWithCommas(stats.treatment_total) }}
      </div>
      <div class="text-2xl mb-4">
        <span class="font-bold">
          Total Patients:
        </span>
        {{ numberWithCommas(stats.cumulative_total) }}
      </div>
    </div>
</template>

<script>
export default {
  name: "HosData",
  props: ["stats"],
  methods: {
    numberWithCommas(number) {
      return number.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ",");
    },
  },
};
</script>
