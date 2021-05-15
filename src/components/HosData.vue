<template>
  <div class="tw-shadow-md tw-bg-blue-100 tw-p-5 tw-text-center tw-rounded">
      <i class="fa fa-ambulance"></i>
      <h3 class="tw-text-3xl tw-text-blue-900 tw-font-bold tw-mb-4">
        Cases
      </h3>

      <div class="tw-text-2xl tw-mb-4">
        <span class="tw-font-bold">
          Current Patients:
        </span>
        {{ numberWithCommas(stats.treatment_total) }}
      </div>
      <div class="tw-text-2xl tw-mb-4">
        <span class="tw-font-bold">
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
