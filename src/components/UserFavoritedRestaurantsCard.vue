<template>
  <!-- User Favorited Restaurants Card -->
  <div class="card">
    <div class="card-header">
      <strong>{{ favoritedRestaurants.length }}</strong> 收藏的餐廳
    </div>
    <div class="card-body">
      <a
        v-for="favoritedRestaurant in favoritedRestaurants"
        :key="favoritedRestaurant.id"
        href="/restaurants/14"
      >
        <img
          :src="favoritedRestaurant.image"
          width="60"
          height="60"
          class="avatar"
        />
      </a>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    favoritedRestaurants: {
      type: Array,
      required: true,
    },
  },
};
</script>