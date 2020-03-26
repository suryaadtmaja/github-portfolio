<template>
  <div
    class="sm:grid lg:grid-flow-row lg:gap-5 lg:grid-cols-3 sm:gap-2 sm:grid-cols-2"
  >
    <div v-for="(i, index) in repos" :key="index" class="card p-4 mt-4">
      <div class="h-20 flex flex-col">
        <h3 class="text-base font-bold">{{ i.name }}</h3>
        <p class="pt-2 text-sm font-light">{{ i.description }}</p>
      </div>
      <div class="mt-10 primary-color justify-end flex flex-row">
        <div v-if="i.language != null" class="flex flex-row">
          <svg
            xmlns="http://www.w3.org/2000/svg"
            width="24"
            height="24"
            fill="currentColor"
            stroke="currentColor"
            stroke-width="2"
            stroke-linecap="round"
            stroke-linejoin="round"
            class="feather feather-circle"
          >
            <circle cx="12" cy="12" r="10" />
          </svg>
          <div class="ml-2 text-base font-light">{{ i.language }}</div>
        </div>
        <div v-if="i.stargazers_count > 0" class="ml-5 flex flex-row">
          <svg
            xmlns="http://www.w3.org/2000/svg"
            width="24"
            height="24"
            fill="currentColor"
            stroke="currentColor"
            stroke-width="2"
            stroke-linecap="round"
            stroke-linejoin="round"
            class="feather feather-star"
          >
            <path
              d="M12 2l3.09 6.26L22 9.27l-5 4.87 1.18 6.88L12 17.77l-6.18 3.25L7 14.14 2 9.27l6.91-1.01L12 2z"
            />
          </svg>
          <h3 class="ml-2 text-base font-light">{{ i.stargazers_count }}</h3>
        </div>
      </div>
    </div>
    <Observer @intersect="fetchRepo" />
  </div>
</template>
<script>
import Observer from './Observer'

export default {
  components: {
    Observer
  },
  props: {
    username: {
      type: String,
      required: true
    }
  },
  data() {
    return {
      repos: [],
      page: 1
    }
  },
  methods: {
    async fetchRepo() {
      const res = await fetch(
        `https://api.github.com/users/${this.username}/repos?page=${this.page}&per_page=20`
      )
      this.page++
      const items = await res.json()
      this.repos = [...this.repos, ...items]
    }
  }
}
</script>

<style scoped>
.card {
  min-width: 300px;
  min-height: 150px;
  @apply max-w-sm bg-gray-300 rounded-sm;
}
.primary-color {
  color: #dd7e7e;
}
</style>
