<template>
  <v-row v-if="selectedUser" no-gutters>
    <v-col cols="12">
      <v-card ref="form">
        <v-card-text>
          <template v-for="[key, value] in Object.entries(selectedUser)">
            <!-- TODO Спрятал объекты, для упрощения взаимодействия с моделью -->
            <v-text-field
              v-if="typeof value !== 'object'"
              :key="key"
              :value="value"
              :label="key"
              @input="$emit('input', { key, value: $event })"
            />
          </template>
        </v-card-text>
      </v-card>
    </v-col>
  </v-row>
</template>

<script>
  export default {
    name: 'EditUser',

    props: {
      selectedUser: {
        type: Object,
        default: null,
      },
    },
  }
</script>