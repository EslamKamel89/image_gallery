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
    <div v-for="photo in photos" :key="photo.id">
      <div class="photo" @click="deletePhoto(photo.id)">
        <!-- An image goes here -->
        <img :src="photo.img" alt="photo not found" />
        <button
          @click.stop="toggleFavorite(photo.id)"
          class="favorite-button"
          :class="{ active: photo.isFavorite }"
        >
          ★
        </button>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { ref } from 'vue'
import pr from './utils/pr'
type Photo = {
  id: number
  img: string
  isFavorite: boolean
}
export default {
  setup() {
    // Keep track of the list of photos
    const photos = ref<Photo[]>([])
    // We need a ref for the currently entered URL
    const newPhotoUrl = ref<string>('')
    const addPhoto = () => {
      if (newPhotoUrl.value == '') return
      photos.value.push({ id: Math.random(), img: newPhotoUrl.value, isFavorite: false })
      newPhotoUrl.value = ''
    }
    const toggleFavorite = (id: number) => {
      const index = photos.value.findIndex((photo) => photo.id === id)
      photos.value[index].isFavorite = !photos.value[index].isFavorite
    }
    const deletePhoto = (id: number) => {
      pr('deletePhoto')
      photos.value = photos.value.filter((photo) => photo.id !== id)
    }
    return {
      addPhoto,
      toggleFavorite,
      photos,
      newPhotoUrl,
      pr,
      deletePhoto,
    }
  },
}
</script>

<style></style>
