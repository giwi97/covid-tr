<template>
  <select @change="onChange()"
    v-model="selected"
    class="tw-form-select tw-mt-10 tw-block tw-w-full tw-border tw-p-3 tw-rounded"
  >
    <option value="0">Select Hospital</option>
    <option v-for="hospital in hospitals" :value="hospital.id">
      {{ hospital.hospital.name }}
    </option>
  </select>
</template>

<script>
export default {
  name: "HospitalSelect",
  props: ["hospitals"],
  data() {
    return {
      selected: 0,
    };
  },
  methods: {
      onChange() {
          const hospital = this.hospitals.find((item) => item.id === this.selected)
          console.log(hospital)
          this.$emit('get-hospital', hospital)
      }
  }
};
</script>
