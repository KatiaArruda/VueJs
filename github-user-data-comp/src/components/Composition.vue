<script setup>
import { reactive, computed } from 'vue'

const state = reactive({
  login: 'login',
  name: 'name',
  bio: 'bio',
  company: 'company',
  avatar_url: 'https://unsplash.it/800/600',
  searchInput: '',
})

const avatarUrl = computed(() => state.avatar_url)

async function fetchGithubUser() {
  const res = await fetch(`https://api.github.com/users/${state.searchInput}`)
  const { login, name, bio, company, avatar_url } = await res.json()

  state.login = login
  state.name = name
  state.bio = bio
  state.company = company
  state.avatar_url = avatar_url
}
</script>

<template>
  <h1>Query users on GitHub</h1>
  <input type="text" v-model="state.searchInput" />
  <button v-on:click="fetchGithubUser">Query</button>
  <img v-bind:src="avatarUrl" />
  <strong>@{{ state.login }}</strong>
  <h2>{{ state.name }}</h2>
  <h3>{{ state.company }}</h3>
  <span>{{ state.bio }}</span>
</template>
