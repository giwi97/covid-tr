<template>
  <div class="tw-text-center">
    <h2 class="tw-text-3xl tw-font-bold">
      {{ text }}
    </h2>
    <div class="tw-text-2xl tw-mt-4 tw-mb-10">
      {{ timestamp }}
    </div>
  </div>
</template>

<script>
import moment from 'moment'

export default {
  name: "DataTitle",
  props: ["text", "dataDate"],
  computed: {
      timestamp: function() {
          return moment(this.dataDate).format('MMMM Do YYYY, h:mm:ss a')
      }
  }
};
</script>
