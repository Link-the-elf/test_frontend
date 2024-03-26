<template>
  <v-card v-if="selectedUser">
    <v-card-title>
      {{ selectedUser.firstname }} {{ selectedUser.lastname }}
    </v-card-title>

    <v-card-text>
      <div
        v-for="[key, value] in Object.entries(selectedUser)"
        :key="key"
      >
        <strong>{{ key }}:</strong>
        
        <!-- TODO Спрятал объекты, для упрощения взаимодействия с моделью -->
        <span v-if="typeof value !== 'object'">
          {{ value }}
        </span>
      </div>
    </v-card-text>
  </v-card>
</template>

<script>
  export default {
    name: 'UserInfo',

    props: {
      selectedUser: {
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