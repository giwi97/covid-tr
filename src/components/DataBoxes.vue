<template>
  <div class="grid md:grid-cols-2 gap-4">
    <div class="shadow-md bg-blue-100 p-10 text-center rounded">
      <i class="fa fa-ambulance"></i>
      <h3 class="text-3xl text-blue-900 font-bold mb-4">
        Cases
      </h3>

      <div class="text-2xl mb-4">
        <span class="font-bold">
          New:
        </span>
        {{ numberWithCommas(stats.local_new_cases) }}
      </div>
      <div class="text-2xl mb-4">
        <span class="font-bold">
          Total:
        </span>
        {{ numberWithCommas(stats.local_total_cases) }}
      </div>
    </div>

    <div class="shadow-md bg-blue-100 p-10 text-center rounded">
      <i class="fa fa-bed"></i>
      <h3 class="text-3xl text-blue-900 font-bold mb-4">
        Deaths
      </h3>

      <div class="text-2xl mb-4">
        <span class="font-bold">
          New:
        </span>
        {{ numberWithCommas(stats.local_new_deaths) }}
      </div>
      <div class="text-2xl mb-4">
        <span class="font-bold">
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
