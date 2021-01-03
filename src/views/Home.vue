<template>
  <div>
    <bounce-loader :loading="isLoading" :color="'#68d391'" :size="100"/>
    <px-asset-table v-if="!isLoading" v-bind:assets = "assets"/>
  </div>
</template>

<script>
import api from '@/api'
import PxAssetTable from '@/components/PxAssetTable.vue'

export default {
  name: 'Home',
  components: { PxAssetTable },
  data () {
    return {
      assets: [],
      isLoading: false
    }
  },
  created () {
    this.isLoading = true
    api.getAssets()
      .then(assets => (this.assets = assets))
      .finally(() => this.isLoading = false)
  }
}
</script>
