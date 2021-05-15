<template>
  <div class="tw-grid md:tw-grid-cols-2 tw-gap-4">
    <div class="tw-shadow-md tw-bg-blue-100 tw-p-10 tw-text-center tw-rounded">
      <i class="fa fa-ambulance"></i>
      <h3 class="tw-text-3xl tw-text-blue-900 tw-font-bold tw-mb-4">
        Cases
      </h3>

      <div class="tw-text-2xl tw-mb-4">
        <span class="tw-font-bold">
          New:
        </span>
        {{ numberWithCommas(stats.local_new_cases) }}
      </div>
      <div class="tw-text-2xl tw-mb-4">
        <span class="tw-font-bold">
          Total:
        </span>
        {{ numberWithCommas(stats.local_total_cases) }}
      </div>
    </div>

    <div class="tw-shadow-md tw-bg-red-300 tw-p-10 tw-text-center tw-rounded">
      <i class="fa fa-bed"></i>
      <h3 class="tw-text-3xl tw-text-blue-900 tw-font-bold tw-mb-4">
        Deaths
      </h3>

      <div class="tw-text-2xl tw-mb-4">
        <span class="tw-font-bold">
          New:
        </span>
        {{ numberWithCommas(stats.local_new_deaths) }}
      </div>
      <div class="tw-text-2xl tw-mb-4">
        <span class="tw-font-bold">
          Total:
        </span>
        {{ numberWithCommas(stats.local_deaths) }}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "DataBoxes",
  props: ["stats"],
  methods: {
      numberWithCommas(number) {
          return number.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ',')
      }
  }
};
</script>
