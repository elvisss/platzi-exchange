<template>
  <div>
    <bounce-loader :loading="loading" color="#68d391" :size="100" />
    <template v-if="!loading">
      <template v-if="error">
        <h2>Error</h2>
      </template>
      <template v-else>
        <px-assets-table :assets="assets" />
      </template>
    </template>
  </div>
</template>

<script>
import api from '@/api'
import PxAssetsTable from '@/components/PxAssetsTable'

export default {
  name: 'Home',
  components: {
    PxAssetsTable
  },

  data() {
    return {
      assets: [],
      loading: false,
      error: false
    }
  },

  created() {
    this.loading = true
    api
      .getAssets()
      .then(data => (this.assets = data))
      .catch(() => (this.error = true))
      .finally(() => (this.loading = false))
  }
}
</script>
