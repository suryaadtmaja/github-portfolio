<template>
  <div class="min-h-screen">
    <div class="max-w-screen-xl mx-auto px-4">
      <div class="pt-12 flex flex-col">
        <h3 class="text-lg font-bold">Filsuck</h3>
        <p class="text-sm font-light">A Human</p>
      </div>
      <div class="pt-12">
        <Repository />
      </div>
    </div>
  </div>
</template>

<script>
import Repository from '@/components/Repository'
export default {
  components: {
    Repository
  }
}
</script>
