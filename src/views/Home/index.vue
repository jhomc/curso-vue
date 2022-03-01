<template>
  <custom-header
    @login="handleLogin()"
    @create-account="handleAccountCreate()"
  />
  <contact />
  <div class="flex justify-center py-10 bg-branding-gray">
    <p class="font-medium text-center text-gray-800">feedbacker &copy; 2021</p>
  </div>
</template>

<script>
import { onMounted } from 'vue'
import { useRouter } from 'vue-router'
import CustomHeader from './CustomHeader.vue'
import Contact from './Contact.vue'
import useModal from '../../hooks/useModal'

export default {
  components: { CustomHeader, Contact },
  setup() {
    const router = useRouter()
    const modal = useModal()

    onMounted(() => {
      const token = window.localStorage.getItem('token')
      if (token) {
        router.push({ name: 'Feedbacks' })
      }
    })

    function handleLogin() {
      modal.open({
        component: 'ModalLogin'
      })
    }

    function handleAccountCreate() {}

    return {
      handleLogin,
      handleAccountCreate
    }
  }
}
</script>
