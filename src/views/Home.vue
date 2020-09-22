<template>
  <div>
    <template v-if="error">
      <h2>Error</h2>
    </template>
    <template v-else>
      <px-assets-table :assets="assets" />
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
      error: false
    }
  },

  created() {
    api
      .getAssets()
      .then(data => (this.assets = data))
      .catch(() => (this.error = true))
  }
}
</script>
