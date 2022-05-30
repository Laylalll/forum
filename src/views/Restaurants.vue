<template>
  <div class="container py-5">
    <!-- 使用 NavTabs 元件 -->
    <NavTabs />
    <!-- 餐廳類別標籤 RestaurantsNavPills -->
    <RestaurantsNavPills :categories="categories" />

    <!-- 餐廳卡片 RestaurantCard-->
    <div class="row">
      <RestaurantCard
        v-for="restaurant in restaurants"
        :key="restaurant.id"
        :initial-restaurant="restaurant"
      />
    </div>

    <!-- 分頁標籤 RestaurantPagination -->
    <RestaurantsPagination
      v-if="totalPage.length > 1"
      :category-id="categoryId"
      :current-page="currentPage"
      :previous-page="previousPage"
      :total-page="totalPage"
      :next-page="nextPage"
    />
  </div>
</template>

<script>
import NavTabs from "./../components/NavTabs.vue";
import RestaurantCard from "./../components/RestaurantCard.vue";
import RestaurantsNavPills from "./../components/RestaurantsNavPills.vue";
import RestaurantsPagination from "./../components/RestaurantsPagination.vue";

const dummyData = {
  restaurants: [
    {
      id: 1,
      name: "Silas Corwin",
      tel: "551-483-8085",
      address: "2569 Block Mission",
      opening_hours: "08:00",
      description: "qui quisquam hic",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=55.2714054539011",
      viewCounts: 0,
      createdAt: "2022-04-25T16:40:51.000Z",
      updatedAt: "2022-04-25T16:40:51.000Z",
      CategoryId: 5,
      Category: {
        id: 5,
        name: "素食料理",
        createdAt: "2022-04-25T16:40:51.000Z",
        updatedAt: "2022-04-25T16:40:51.000Z",
      },
      isFavorited: false,
      isLiked: false,
    },
    {
      id: 2,
      name: "Dr. Bill Baumbach",
      tel: "1-965-317-0756",
      address: "2132 Gaylord Grove",
      opening_hours: "08:00",
      description: "Est et labore quasi consequatur nisi velit eum.\nVe",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=13.967577181543156",
      viewCounts: 0,
      createdAt: "2022-04-25T16:40:51.000Z",
      updatedAt: "2022-04-25T16:40:51.000Z",
      CategoryId: 3,
      Category: {
        id: 3,
        name: "義大利料理",
        createdAt: "2022-04-25T16:40:51.000Z",
        updatedAt: "2022-04-25T16:40:51.000Z",
      },
      isFavorited: false,
      isLiked: false,
    },
    {
      id: 3,
      name: "Jarrett Walsh",
      tel: "1-578-629-8903 x96347",
      address: "96680 Linda Fall",
      opening_hours: "08:00",
      description: "fugit sapiente sint",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=75.8608414321313",
      viewCounts: 0,
      createdAt: "2022-04-25T16:40:51.000Z",
      updatedAt: "2022-04-25T16:40:51.000Z",
      CategoryId: 3,
      Category: {
        id: 3,
        name: "義大利料理",
        createdAt: "2022-04-25T16:40:51.000Z",
        updatedAt: "2022-04-25T16:40:51.000Z",
      },
      isFavorited: false,
      isLiked: false,
    },
    {
      id: 4,
      name: "Sterling Ondricka",
      tel: "1-822-009-8110 x7402",
      address: "777 Morar Well",
      opening_hours: "08:00",
      description: "magni deleniti ut",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=23.484880664213147",
      viewCounts: 0,
      createdAt: "2022-04-25T16:40:51.000Z",
      updatedAt: "2022-04-25T16:40:51.000Z",
      CategoryId: 1,
      Category: {
        id: 1,
        name: "中式料理",
        createdAt: "2022-04-25T16:40:51.000Z",
        updatedAt: "2022-04-25T16:40:51.000Z",
      },
      isFavorited: false,
      isLiked: false,
    },
    {
      id: 5,
      name: "Maida Ankunding",
      tel: "(457) 456-6127 x9673",
      address: "3807 Rylan Loop",
      opening_hours: "08:00",
      description: "Soluta sed cum facilis sequi eius a mollitia nihil",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=93.11795001819398",
      viewCounts: 0,
      createdAt: "2022-04-25T16:40:51.000Z",
      updatedAt: "2022-04-25T16:40:51.000Z",
      CategoryId: 3,
      Category: {
        id: 3,
        name: "義大利料理",
        createdAt: "2022-04-25T16:40:51.000Z",
        updatedAt: "2022-04-25T16:40:51.000Z",
      },
      isFavorited: false,
      isLiked: false,
    },
    {
      id: 6,
      name: "Elsa Koss",
      tel: "(750) 464-5592",
      address: "5883 Lehner Stream",
      opening_hours: "08:00",
      description: "Sed natus recusandae tempore blanditiis. Sint faci",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=54.74380325381185",
      viewCounts: 0,
      createdAt: "2022-04-25T16:40:51.000Z",
      updatedAt: "2022-04-25T16:40:51.000Z",
      CategoryId: 4,
      Category: {
        id: 4,
        name: "墨西哥料理",
        createdAt: "2022-04-25T16:40:51.000Z",
        updatedAt: "2022-04-25T16:40:51.000Z",
      },
      isFavorited: false,
      isLiked: false,
    },
    {
      id: 7,
      name: "Jasmin Wiza",
      tel: "(689) 286-0825 x594",
      address: "889 Foster Grove",
      opening_hours: "08:00",
      description: "Ut molestiae nobis a numquam enim eveniet officiis",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=81.5034839074767",
      viewCounts: 0,
      createdAt: "2022-04-25T16:40:51.000Z",
      updatedAt: "2022-04-25T16:40:51.000Z",
      CategoryId: 5,
      Category: {
        id: 5,
        name: "素食料理",
        createdAt: "2022-04-25T16:40:51.000Z",
        updatedAt: "2022-04-25T16:40:51.000Z",
      },
      isFavorited: false,
      isLiked: false,
    },
    {
      id: 8,
      name: "Shany Cremin",
      tel: "923.146.1176 x0869",
      address: "40314 Reinger Throughway",
      opening_hours: "08:00",
      description: "Consectetur in ut.",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=99.89474724153646",
      viewCounts: 0,
      createdAt: "2022-04-25T16:40:51.000Z",
      updatedAt: "2022-04-25T16:40:51.000Z",
      CategoryId: 3,
      Category: {
        id: 3,
        name: "義大利料理",
        createdAt: "2022-04-25T16:40:51.000Z",
        updatedAt: "2022-04-25T16:40:51.000Z",
      },
      isFavorited: false,
      isLiked: false,
    },
    {
      id: 9,
      name: "Myrna Wuckert",
      tel: "413-157-1997 x191",
      address: "954 Cesar Extensions",
      opening_hours: "08:00",
      description: "Earum sit neque. Blanditiis nostrum dignissimos ul",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=99.11260009231549",
      viewCounts: 0,
      createdAt: "2022-04-25T16:40:51.000Z",
      updatedAt: "2022-04-25T16:40:51.000Z",
      CategoryId: 3,
      Category: {
        id: 3,
        name: "義大利料理",
        createdAt: "2022-04-25T16:40:51.000Z",
        updatedAt: "2022-04-25T16:40:51.000Z",
      },
      isFavorited: false,
      isLiked: false,
    },
    {
      id: 10,
      name: "Ms. Frieda Oberbrunner",
      tel: "456.257.5860 x66895",
      address: "8013 Volkman Estates",
      opening_hours: "08:00",
      description: "molestiae",
      image:
        "https://loremflickr.com/320/240/restaurant,food/?random=94.35927327253846",
      viewCounts: 0,
      createdAt: "2022-04-25T16:40:51.000Z",
      updatedAt: "2022-04-25T16:40:51.000Z",
      CategoryId: 5,
      Category: {
        id: 5,
        name: "素食料理",
        createdAt: "2022-04-25T16:40:51.000Z",
        updatedAt: "2022-04-25T16:40:51.000Z",
      },
      isFavorited: false,
      isLiked: false,
    },
  ],
  categories: [
    {
      id: 1,
      name: "中式料理",
      createdAt: "2022-04-25T16:40:51.000Z",
      updatedAt: "2022-04-25T16:40:51.000Z",
    },
    {
      id: 2,
      name: "日本料理",
      createdAt: "2022-04-25T16:40:51.000Z",
      updatedAt: "2022-04-25T16:40:51.000Z",
    },
    {
      id: 3,
      name: "義大利料理",
      createdAt: "2022-04-25T16:40:51.000Z",
      updatedAt: "2022-04-25T16:40:51.000Z",
    },
    {
      id: 4,
      name: "墨西哥料理",
      createdAt: "2022-04-25T16:40:51.000Z",
      updatedAt: "2022-04-25T16:40:51.000Z",
    },
    {
      id: 5,
      name: "素食料理",
      createdAt: "2022-04-25T16:40:51.000Z",
      updatedAt: "2022-04-25T16:40:51.000Z",
    },
    {
      id: 6,
      name: "美式料理",
      createdAt: "2022-04-25T16:40:51.000Z",
      updatedAt: "2022-04-25T16:40:51.000Z",
    },
    {
      id: 7,
      name: "複合式料理",
      createdAt: "2022-04-25T16:40:51.000Z",
      updatedAt: "2022-04-25T16:40:51.000Z",
    },
  ],
  categoryId: "",
  page: 1,
  totalPage: [1, 2, 3, 4, 5],
  prev: 1,
  next: 2,
};

export default {
  name: "Restaurants",
  components: {
    NavTabs, // NavTabs: NavTabs的縮寫
    RestaurantCard,
    RestaurantsNavPills,
    RestaurantsPagination,
  },

  data() {
    return {
      // default data
      restaurants: [],
      categories: [],
      categoryId: -1, //待覆寫掉
      currentPage: 1,
      totalPage: [],
      previousPage: -1, //待覆寫掉
      nextPage: -1, //待覆寫掉
    };
  },

  created() {
    this.fetchRestaurants();
  },

  methods: {
    fetchRestaurants() {
      const {
        restaurants,
        categories,
        categoryId,
        page,
        totalPage,
        prev,
        next,
      } = dummyData;

      this.restaurants = restaurants;
      this.categories = categories;
      this.categoryId = categoryId;
      this.currentPage = page;
      this.totalPage = totalPage;
      this.previousPage = prev;
      this.nextPage = next;
    },
  },
};
</script>
