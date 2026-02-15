<template>
  <q-page padding>

    <div class="text-h5 q-mb-md">
      Backend API Demo
    </div>

    <q-btn
      label="Fetch API"
      color="primary"
      @click="fetchData"
      class="q-mb-md"
    />

    <div v-if="apiData">
      <pre>{{ apiData }}</pre>
    </div>

  </q-page>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import axios from 'axios'

const apiData = ref(null)

const fetchData = async () => {
  try {
    const res = await axios.get(
      import.meta.env.VITE_API_URL + '/api/demo'
    )
    apiData.value = res.data
  } catch (err) {
    console.error('API error:', err)
  }
}

onMounted(fetchData)
</script>
