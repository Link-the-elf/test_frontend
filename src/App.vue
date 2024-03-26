<template>
  <v-app>
    <v-main>
      <v-container class="mt-4">
        <v-row>
          <v-col
            cols="12"
            sm="4"
          >
            <UserInfo
              :selected-user="selectedUser" 
              :users="users" 
            />
          </v-col>

          <v-col
            cols="12"
            sm="4"
          >
            <UserSelect
              v-model="selectedUser"
              :users="users"
            />
          </v-col>

          <v-col
            cols="12"
            sm="4"
          >
            <EditUser 
              :selected-user="selectedUser" 
              @input="editValue"
            />
          </v-col>
        </v-row>
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
import UserInfo from '@/components/UserInfo.vue';
import UserSelect from '@/components/UserSelect.vue';
import EditUser from '@/components/EditUser.vue';

export default {
  name: "App",
  
  components: {
    UserInfo,
    UserSelect,
    EditUser,
  },

  data: () => ({
    users: [],
    selectedUser: null,
  }),

  methods: {
    async getUsers() {
      try {
        const response = await fetch('https://fakerapi.it/api/v1/persons?_locale=ru_RU');
        const { data } = await response.json();
        return data;
      } catch (e) {
        console.error(e);
      }
    },

    editValue({ key, value }) {
      this.selectedUser[key] = value;
    }
  },
  
  async mounted() {
    this.users = await this.getUsers();
    [this.selectedUser] = this.users;
  }
};
</script>
