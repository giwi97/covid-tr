<template>
    <select v-model="selected" class="form-select mt-10 block w-full border p-3 rounded">
        <option value="0">Select Hospital</option>
    </select>
</template>

<script>
export default {
    name: 'HospitalSelect',
    props: ['hospitals'],
    data() {
        return {
            selected: 0
        }
    }
}
</script>