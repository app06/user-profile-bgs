<template>
  <div>
    <login v-if="!user.id" @login="login" />
    <profile v-else :user="user" />
  </div>
</template>

<script>
import Login from '~/components/Login'
import Profile from '~/components/Profile'

export default {
  components: { Login, Profile },
  data: () => ({
    user: {
      id: null,
      name: null,
      login: null,
      avatar: null,
      email: null,
    },
  }),
  methods: {
    login(user) {
      this.user = user
    },
  },
}
</script>
