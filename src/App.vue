<template>
  <!-- Form for Adding Photos -->
  <form>
    <input placeholder="Enter image URL" />
    <button type="submit">Add Photo</button>
  </form>

  <!-- Conditional Rendering -->
  <p class="no-photos">No photos added yet. Add some!</p>

  <div class="gallery">
    <!-- List Rendering and Conditional Class Binding -->
    <div class="photo">
      <!-- An image goes here -->
      <button class="favorite-button">★</button>
    </div>
  </div>
</template>

<script lang="ts">
export default {
  setup() {
    // Keep track of the list of photos
    // We need a ref for the currently entered URL
    const addPhoto = () => {
      // Adding photo logic goes here
    }
    const toggleFavorite = () => {
      // Favorite toggling logic
    }

    return {
      addPhoto,
      toggleFavorite,
    }
  },
}
</script>

<style></style>
