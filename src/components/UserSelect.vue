<template>
  <v-autocomplete
    :value="value"
    :items="users"
    label="Выберите пользователя для просмотра детальной информации"
    @input="$emit('input', $event)"
  >
    <template #selection="data">
      {{ data.item.firstname }} {{ data.item.lastname }}
    </template>

    <template #item="data">
      {{ data.item.firstname }} {{ data.item.lastname }}
    </template>
  </v-autocomplete>
</template>

<script>
  export default {
    name: 'UserSelect',

    props: {
      value: {
        type: Object,
        default: null,
      },
      users: {
        type: Array,
        required: true,
      },
    },
  }
</script>