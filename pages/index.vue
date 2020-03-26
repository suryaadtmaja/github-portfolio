<template>
  <div class="min-h-screen">
    <div class="max-w-screen-xl mx-auto px-4">
      <div class="pt-12 flex flex-col">
        <h3 class="text-4xl font-bold">{{ githubData.name }}</h3>
        <p class="text-lg font-light">{{ githubData.bio }}</p>
      </div>
      <div class="pt-12">
        <Repository :username="username" />
      </div>
    </div>
  </div>
</template>

<script>
import Repository from '@/components/Repository'
export default {
  components: {
    Repository
  },
  data() {
    return {
      username: 'filsuck',
      githubData: []
    }
  },
  mounted() {
    this.fetchUser()
  },
  methods: {
    async fetchUser() {
      const res = await this.$axios.get(`${this.username}`)
      this.githubData = res.data
    }
  }
}
</script>
