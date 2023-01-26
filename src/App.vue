<script setup lang="ts">
import { reactive } from 'vue'
import db from './firebase/store'
import { collection, getDocs } from 'firebase/firestore'

const snapshot = await getDocs(collection(db, 'users'))
snapshot.forEach((doc) => users.push(doc.data()))

const users = reactive([])
</script>

<template>
  <div>
    <h1>Users</h1>
  </div>
  <div>
    <div v-for="user in users">
      <p>{{ user.username }}</p>
    </div>
  </div>
</template>
