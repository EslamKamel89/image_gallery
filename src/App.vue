<template>
  <!-- Form for Adding Photos -->
  <form @submit.prevent="addPhoto">
    <input placeholder="Enter image URL" v-model="newPhotoUrl" />
    <button type="submit">Add Photo</button>
  </form>

  <!-- Conditional Rendering -->
  <p v-if="photos?.length === 0" class="no-photos">No photos added yet. Add some!</p>

  <div v-else class="gallery">
    <!-- List Rendering and Conditional Class Binding -->
    <div v-for="photo in photos" :key="photo">
      <div class="photo">
        <!-- An image goes here -->
        <img :src="photo" alt="photo not found" />
        <button @click="toggleFavorite" class="favorite-button">★</button>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { ref } from 'vue'

export default {
  setup() {
    // Keep track of the list of photos
    const photos = ref<string[]>([])
    // We need a ref for the currently entered URL
    const newPhotoUrl = ref<string>('')
    const addPhoto = () => {
      photos.value.push(newPhotoUrl.value)
      newPhotoUrl.value = ''
    }
    const toggleFavorite = () => {}

    return {
      addPhoto,
      toggleFavorite,
      photos,
      newPhotoUrl,
    }
  },
}
</script>

<style></style>
