<template>
  <div class="container py-5">
    <!-- Dashboard -->
    <div>
      <h1>{{ restaurant.name }}</h1>
      <span class="badge badge-secondary mt-1 mb-3">
        {{ restaurant.categoryName }}
      </span>
    </div>

    <hr />

    <ul>
      <li>評論數： {{ restaurant.commentsLength }}</li>
      <li>瀏覽次數： {{ restaurant.viewCounts }}</li>
    </ul>

    <button type="button" class="btn btn-link" @click="$router.back()">
      回上一頁
    </button>
  </div>
</template>

<script>
//postman拿來的假資料
const dummyData = {
  restaurant: {
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
    Comments: [
      {
        id: 1,
        text: "Quis nisi nihil praesentium possimus est omnis.",
        UserId: 2,
        RestaurantId: 1,
        createdAt: "2022-04-25T16:40:51.000Z",
        updatedAt: "2022-04-25T16:40:51.000Z",
        User: {
          id: 2,
          name: "user1",
          email: "user1@example.com",
          password:
            "$2a$10$wp5v.Fpi2HkYsqTQUlCHsec1Xipl.pDxlag2./NHf0w5tqKpSBNkm",
          isAdmin: false,
          image: null,
          createdAt: "2022-04-25T16:40:51.000Z",
          updatedAt: "2022-04-25T16:40:51.000Z",
        },
      },
      {
        id: 101,
        text: "Nam dolor enim dolores aut voluptates alias eaque amet inventore.",
        UserId: 2,
        RestaurantId: 1,
        createdAt: "2022-04-25T16:40:51.000Z",
        updatedAt: "2022-04-25T16:40:51.000Z",
        User: {
          id: 2,
          name: "user1",
          email: "user1@example.com",
          password:
            "$2a$10$wp5v.Fpi2HkYsqTQUlCHsec1Xipl.pDxlag2./NHf0w5tqKpSBNkm",
          isAdmin: false,
          image: null,
          createdAt: "2022-04-25T16:40:51.000Z",
          updatedAt: "2022-04-25T16:40:51.000Z",
        },
      },
      {
        id: 51,
        text: "Eum dolores placeat.",
        UserId: 3,
        RestaurantId: 1,
        createdAt: "2022-04-25T16:40:51.000Z",
        updatedAt: "2022-04-25T16:40:51.000Z",
        User: {
          id: 3,
          name: "user2",
          email: "user2@example.com",
          password:
            "$2a$10$f/i3dNO1tlrE8CyfgcV6HOlqJAXF1e/4RM4RfgIzQARTREVBtZysi",
          isAdmin: false,
          image: null,
          createdAt: "2022-04-25T16:40:51.000Z",
          updatedAt: "2022-04-25T16:40:51.000Z",
        },
      },
    ],
  },
};

export default {
  data() {
    return {
      restaurant: {
        id: -1, //待串API，拿到真實資料後覆寫
        name: "",
        categoryName: "",
        viewCounts: 0,
        commentsLength: 0,
      },
    };
  },

  created() {
    // console.log("params", this.$route.params);
    const { id: restaurantId } = this.$route.params;
    this.fetchRestaurant(restaurantId);
  },

  methods: {
    fetchRestaurant(restaurantId) {
      console.log("fetchRestaurant id", restaurantId); //確認有按照路由去拉對應的資料
      const { id, name, Category, viewCounts, Comments } = dummyData.restaurant;
      this.restaurant = {
        ...this.restaurant,
        id, //id: id
        name, //name: name
        categoryName: Category ? Category.name : "未分類",
        viewCounts, //viewCounts: viewCounts
        commentsLength: Comments.length,
      };
    },
  },
};
</script>