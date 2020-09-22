<template>
  <button
    @click="onClick"
    class="bg-transparent hover:bg-green-500 text-green-700 font-semibold hover:text-white py-2 px-2 border border-green-500 hover:border-transparent rounded"
  >
    <beat-loader :loading="loading" color="#68d391" :size="8" />
    <span v-show="!loading">
      <slot />
    </span>
  </button>
</template>

<script>
export default {
  name: 'PxButton',
  props: {
    loading: {
      type: Boolean,
      default: false
    }
  },
  methods: {
    onClick() {
      this.$emit('custom-click')
    }
  }
}
</script>
