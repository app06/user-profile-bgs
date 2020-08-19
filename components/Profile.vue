<template>
  <v-card class="mx-auto app-card" max-width="344" outlined>
    <v-list-item>
      <v-list-item-content>
        <v-list>
          <v-list-item>
            <v-list-item-content>
              <v-list-item-title>{{ user.email }}</v-list-item-title>
            </v-list-item-content>
          </v-list-item>
          <v-divider></v-divider>
          <v-list-item>
            <v-list-item-content>
              <v-list-item-title>{{ user.name }}</v-list-item-title>
            </v-list-item-content>
          </v-list-item>
        </v-list>
      </v-list-item-content>

      <v-list-item-avatar tile size="80">
        <v-avatar> <img :src="user.avatar" :alt="user.login" /> </v-avatar
      ></v-list-item-avatar>
    </v-list-item>
  </v-card>
</template>

<script>
export default {
  props: {
    user: {
      type: Object,
      required: true,
    },
  },
}
</script>

<style>
.app-card {
  margin-top: 50px;
}
</style>
