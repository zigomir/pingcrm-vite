<template>
  <div>
    <h1 class="mb-8 font-bold text-3xl">
      <inertia-link
        class="text-indigo-400 hover:text-indigo-600"
        :href="UsersRequests.pathFor('list')"
      >
        Users
      </inertia-link>
      <span class="text-indigo-400 font-medium">/</span> Create
    </h1>
    <div class="bg-white rounded shadow overflow-hidden max-w-3xl">
      <user-form
        v-model="form"
        @submit="UsersRequests.create({ form })"
      >
        <div class="px-8 py-4 bg-gray-100 border-t border-gray-200 flex justify-end items-center">
          <loading-button
            :loading="form.processing"
            class="btn-indigo"
            type="submit"
          >
            Create User
          </loading-button>
        </div>
      </user-form>
    </div>
  </div>
</template>

<script>
import Layout from '@/Layouts/Main.vue'
import LoadingButton from '@/Shared/LoadingButton.vue'
import UserForm from './Form.vue'
import UsersRequests from '@/requests/UsersRequests'

export default {
  metaInfo: { title: 'Create User' },
  constants: {
    UsersRequests,
  },
  components: {
    LoadingButton,
    UserForm,
  },
  layout: Layout,
  props: {
    user: {
      type: Object,
      required: true,
    },
  },
  remember: 'form',
  data() {
    return {
      form: this.$inertia.form({
        user: this.user,
      }),
    }
  },
}
</script>
