<script setup>
import { reactive, computed } from 'vue'

const state = reactive({
  login: '',
  name: '',
  bio: '',
  company: '',
  avatar_url: '',
  repositories: [],
  searchInput: '',
})

// Computed property with a fallback
const avatarUrl = computed(
  () => state.avatar_url || 'https://unsplash.it/800/600'
)

async function fetchGithubUser() {
  try {
    const res = await fetch(`https://api.github.com/users/${state.searchInput}`)
    const { login, name, bio, company, avatar_url } = await res.json()

    Object.assign(state, { login, name, bio, company, avatar_url }) // Update state

    fetchUserRepositories(state.searchInput)
  } catch (error) {
    console.error('Error fetching GitHub user:', error)
    // Error handling
  }
}

async function fetchUserRepositories(username) {
  try {
    const res = await fetch(`https://api.github.com/users/${username}/repos`)
    const repositories = await res.json()

    state.repositories = repositories
  } catch (error) {
    console.error('Error fetching repositories:', error)
  }
}
</script>

<template>
  <h1>Query users on GitHub</h1>
  <input type="text" v-model="state.searchInput" />
  <button @click="fetchGithubUser">Query</button>
  <div v-if="state.login !== ''">
    <img :src="avatarUrl" alt="Avatar" />
    <strong>@{{ state.login }}</strong>
    <h2>{{ state.name }}</h2>
    <h3>{{ state.company }}</h3>
    <span>{{ state.bio }}</span>
  </div>
  <div>
    <article v-for="repo in state.repositories" :key="repo.id">
      <h1>{{ repo.name }}</h1>
      <p>{{ repo.description }}</p>
      <a href="repo.html_url" target="_blank">consult on github</a>
    </article>
  </div>
</template>
