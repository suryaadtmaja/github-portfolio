<template>
  <div>
    <div v-for="(i, index) in repo" :key="index" class="card p-4 mt-4">
      <div class="flex flex-col">
        <h3 class="text-base font-bold">{{ i.name }}</h3>
        <p class="pt-2 text-sm font-light">{{ i.description }}</p>
      </div>
      <div class="pt-10 justify-end flex flex-row">
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
          <h3 class="ml-2 text-base font-light">4.7k</h3>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  props: {
    repo: {
      type: Array,
      required: true
    }
  },
  data() {
    return {
      repos: [
        {
          name: 'Vue Js',
          description:
            'Vue.js is a progressive, incrementally-adoptable JavaScript framework for building UI on the web. http://vuejs.org'
        }
      ]
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
</style>
