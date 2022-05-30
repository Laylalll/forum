<template>
  <div class="container py-5">
    <!-- 使用 NavTabs 元件 -->
    <NavTabs />
    <h1 class="mt-5">人氣餐廳</h1>
    <hr />

    <div
      v-for="restaurant in restaurants"
      :key="restaurant.id"
      class="card mb-3"
      style="max-width: 540px; margin: auto"
    >
      <div class="row no-gutters">
        <div class="col-md-4">
          <router-link
            :to="{ name: 'restaurant', params: { id: restaurant.id } }"
          >
            <img class="card-img" :src="restaurant.image" />
          </router-link>
        </div>
        <div class="col-md-8">
          <div class="card-body">
            <h5 class="card-title">{{ restaurant.name }}</h5>
            <span class="badge badge-secondary"
              >收藏數：{{ restaurant.FavoriteCount }}</span
            >
            <p class="card-text">
              {{ restaurant.description }}
            </p>
            <router-link
              :to="{ name: 'restaurant', params: { id: restaurant.id } }"
              class="btn btn-primary mr-2"
              >Show</router-link
            >

            <button
              v-if="restaurant.isFavorited"
              @click.stop.prevent="deleteFavorite(restaurant.id)"
              type="button"
              class="btn btn-danger mr-2"
            >
              移除最愛
            </button>
            <button
              v-else
              @click.stop.prevent="addFavorite(restaurant.id)"
              type="button"
              class="btn btn-primary"
            >
              加到最愛
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import NavTabs from "./../components/NavTabs.vue";

const dummyData = {
  restaurants: [
    {
      id: 50,
      name: "Meaghan Grady",
      tel: "904-103-1795",
      address: "678 Melvin Ford",
      opening_hours: "08:00",
      description: "voluptatem quidem est",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=9.869209350099162",
      viewCounts: 0,
      createdAt: "2022-04-25T16:40:51.000Z",
      updatedAt: "2022-04-25T16:40:51.000Z",
      CategoryId: 5,
      FavoritedUsers: [],
      isFavorited: false,
      FavoriteCount: 0,
    },
    {
      id: 49,
      name: "Prince Barton MD",
      tel: "428-737-2678",
      address: "98440 Franecki Green",
      opening_hours: "08:00",
      description: "Dolores doloremque suscipit corrupti facere ipsum.",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=90.71733084189357",
      viewCounts: 0,
      createdAt: "2022-04-25T16:40:51.000Z",
      updatedAt: "2022-04-25T16:40:51.000Z",
      CategoryId: 4,
      FavoritedUsers: [],
      isFavorited: false,
      FavoriteCount: 0,
    },
    {
      id: 48,
      name: "Ross Raynor",
      tel: "1-028-408-1232",
      address: "773 Bauch Ways",
      opening_hours: "08:00",
      description: "Expedita quaerat sunt totam aut quidem ea ut et au",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=92.00351165548636",
      viewCounts: 0,
      createdAt: "2022-04-25T16:40:51.000Z",
      updatedAt: "2022-04-25T16:40:51.000Z",
      CategoryId: 2,
      FavoritedUsers: [],
      isFavorited: false,
      FavoriteCount: 0,
    },
    {
      id: 47,
      name: "Winifred Leffler",
      tel: "900.227.3095 x1079",
      address: "114 Rolando Coves",
      opening_hours: "08:00",
      description: "Aut repudiandae corporis dolor quam et nihil qui. ",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=27.59895589107677",
      viewCounts: 0,
      createdAt: "2022-04-25T16:40:51.000Z",
      updatedAt: "2022-04-25T16:40:51.000Z",
      CategoryId: 2,
      FavoritedUsers: [],
      isFavorited: false,
      FavoriteCount: 0,
    },
    {
      id: 46,
      name: "Cristal Block",
      tel: "1-481-314-6013 x1884",
      address: "20038 Davion Drive",
      opening_hours: "08:00",
      description: "Voluptates temporibus aperiam dolores ab fuga ipsa",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=12.715071745044781",
      viewCounts: 0,
      createdAt: "2022-04-25T16:40:51.000Z",
      updatedAt: "2022-04-25T16:40:51.000Z",
      CategoryId: 2,
      FavoritedUsers: [],
      isFavorited: false,
      FavoriteCount: 0,
    },
    {
      id: 45,
      name: "Misty Feeney",
      tel: "1-412-904-7768",
      address: "80536 Collins Mountain",
      opening_hours: "08:00",
      description: "rerum odit et",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=82.17807730635175",
      viewCounts: 0,
      createdAt: "2022-04-25T16:40:51.000Z",
      updatedAt: "2022-04-25T16:40:51.000Z",
      CategoryId: 3,
      FavoritedUsers: [],
      isFavorited: false,
      FavoriteCount: 0,
    },
    {
      id: 44,
      name: "Coy Leuschke",
      tel: "1-492-911-5062 x47595",
      address: "509 Noemi Passage",
      opening_hours: "08:00",
      description: "Aut quia ex deleniti nemo sapiente quaerat illo. T",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=49.783061839224494",
      viewCounts: 0,
      createdAt: "2022-04-25T16:40:51.000Z",
      updatedAt: "2022-04-25T16:40:51.000Z",
      CategoryId: 3,
      FavoritedUsers: [],
      isFavorited: false,
      FavoriteCount: 0,
    },
    {
      id: 43,
      name: "Jordyn Haag",
      tel: "1-837-547-4769 x2916",
      address: "58173 Pagac Rapids",
      opening_hours: "08:00",
      description: "Ut accusantium dolorum cupiditate qui qui et nemo.",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=51.06764531607286",
      viewCounts: 0,
      createdAt: "2022-04-25T16:40:51.000Z",
      updatedAt: "2022-04-25T16:40:51.000Z",
      CategoryId: 1,
      FavoritedUsers: [],
      isFavorited: false,
      FavoriteCount: 0,
    },
    {
      id: 42,
      name: "Easton Langosh",
      tel: "(785) 287-4629 x4896",
      address: "9552 Brielle Junctions",
      opening_hours: "08:00",
      description: "Ut corporis ratione debitis autem excepturi volupt",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=8.621719750837409",
      viewCounts: 0,
      createdAt: "2022-04-25T16:40:51.000Z",
      updatedAt: "2022-04-25T16:40:51.000Z",
      CategoryId: 1,
      FavoritedUsers: [],
      isFavorited: false,
      FavoriteCount: 0,
    },
    {
      id: 41,
      name: "Romaine Weissnat",
      tel: "1-291-987-8549",
      address: "02381 Franecki Road",
      opening_hours: "08:00",
      description: "Debitis omnis sed natus velit aut dolore autem rer",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=24.83868332240484",
      viewCounts: 0,
      createdAt: "2022-04-25T16:40:51.000Z",
      updatedAt: "2022-04-25T16:40:51.000Z",
      CategoryId: 3,
      FavoritedUsers: [],
      isFavorited: false,
      FavoriteCount: 0,
    },
  ],
};

export default {
  name: "RestaurantsTop",
  components: {
    NavTabs, // NavTabs: NavTabs的縮寫
  },

  data() {
    return {
      restaurants: [], //預設值
    };
  },

  created() {
    this.fetchTopRestaurants(); //載入資料
  },

  methods: {
    fetchTopRestaurants() {
      this.restaurants = dummyData.restaurants;
    },

    deleteFavorite(restaurantId) {
      this.restaurants = this.restaurants.map((restaurant) => {
        // 掃描陣列，回傳所有id不符合的餐廳原有資料
        if (restaurant.id !== restaurantId) {
          return restaurant;
        }
        // 掃描陣列，將id符合的餐廳資料修改
        return {
          ...restaurant,
          FavoriteCount: restaurant.FavoriteCount - 1,
          isFavorited: false,
        };
      });
    },

    addFavorite(restaurantId) {
      this.restaurants = this.restaurants.map((restaurant) => {
        // 掃描陣列，回傳所有id不符合的餐廳原有資料
        if (restaurant.id !== restaurantId) {
          return restaurant;
        }
        // 掃描陣列，將id符合的餐廳資料修改
        return {
          ...restaurant,
          FavoriteCount: restaurant.FavoriteCount + 1,
          isFavorited: true,
        };
      });
    },
  },
};
</script>
