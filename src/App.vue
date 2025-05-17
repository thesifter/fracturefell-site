<script setup lang="ts">
import { ref, onMounted } from 'vue'

const message = ref('')
const loading = ref(true)

onMounted(async () => {
  console.log('🔄 onMounted fired, starting fetch to /api')

  try {
    const response = await fetch('/api')
    console.log('✅ Fetch response:', response)

    const data = await response.json()
    console.log('✅ Parsed data:', data)

    message.value = data.message
  } catch (error) {
    console.error('❌ Fetch failed:', error)
    message.value = 'Failed to fetch from API.'
  } finally {
    loading.value = false
  }
})
</script>
