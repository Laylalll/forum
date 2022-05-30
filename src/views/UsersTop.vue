<template>
  <div class="container py-5">
    <!-- 使用 NavTabs 元件 -->
    <NavTabs />
    <h1 class="mt-5">美食達人</h1>
    <hr />
    <!-- 達人卡片 UsersTopCard-->
    <div class="row text-center">
      <!-- <UsersTopCard v-for="user in users" :key="user.id" :initial-user="user" /> -->
      <div v-for="user in users" :key="user.id" class="col-3">
        <router-link :to="{ name: 'user', params: { id: user.id } }">
          <img :src="user.image" width="140px" height="140px" />
        </router-link>
        <h2>{{ user.name }}</h2>
        <span class="badge badge-secondary"
          >追蹤人數：{{ user.FollowerCount }}</span
        >
        <p class="mt-3">
          <button
            v-if="user.isFollowed"
            @click.stop.prevent="deleteFollowing(user.id)"
            type="button"
            class="btn btn-danger"
          >
            取消追蹤
          </button>
          <button
            v-else
            @click.stop.prevent="addFollowing(user.id)"
            type="button"
            class="btn btn-primary"
          >
            追蹤
          </button>
        </p>
      </div>
    </div>
  </div>
</template>

<script>
import NavTabs from "./../components/NavTabs.vue";
// import UsersTopCard from "./../components/UsersTopCard.vue";

const dummyData = {
  users: [
    {
      id: 1,
      name: "root",
      email: "root@example.com",
      password: "$2a$10$deyCFaswbP9U87IBskJQHu9wbEbniPZVGU6nh4EAw1IhRtYm92sXu",
      isAdmin: true,
      image:
        "https://i.pinimg.com/originals/e2/63/8e/e2638e1c42f2d58fcd07dcb1dc765d25.jpg",
      createdAt: "2022-04-25T16:40:51.000Z",
      updatedAt: "2022-04-25T16:40:51.000Z",
      Followers: [],
      FollowerCount: 0,
      isFollowed: false,
    },
    {
      id: 2,
      name: "user1",
      email: "user1@example.com",
      password: "$2a$10$wp5v.Fpi2HkYsqTQUlCHsec1Xipl.pDxlag2./NHf0w5tqKpSBNkm",
      isAdmin: false,
      image:
        "https://i.pinimg.com/originals/36/70/04/367004cabbed1ea990b7a4757847333b.jpg",
      createdAt: "2022-04-25T16:40:51.000Z",
      updatedAt: "2022-04-25T16:40:51.000Z",
      Followers: [],
      FollowerCount: 0,
      isFollowed: false,
    },
    {
      id: 3,
      name: "user2",
      email: "user2@example.com",
      password: "$2a$10$f/i3dNO1tlrE8CyfgcV6HOlqJAXF1e/4RM4RfgIzQARTREVBtZysi",
      isAdmin: false,
      image:
        "https://i.pinimg.com/originals/e0/b2/a9/e0b2a93142d000350c16211f91c14495.jpg",
      createdAt: "2022-04-25T16:40:51.000Z",
      updatedAt: "2022-04-25T16:40:51.000Z",
      Followers: [],
      FollowerCount: 0,
      isFollowed: false,
    },
  ],
};

export default {
  name: "UsersTop",
  components: {
    NavTabs, // NavTabs: NavTabs的縮寫
    // UsersTopCard,
  },

  data() {
    return {
      // default data
      users: [],
    };
  },

  created() {
    this.fetchTopUsers();
  },

  methods: {
    fetchTopUsers() {
      this.users = dummyData.users;
    },

    deleteFollowing(userId) {
      this.users = this.users.map((user) => {
        if (user.id !== userId) {
          return user;
        } else {
          return {
            ...user, // 保留原有資料
            FollowerCount: user.FollowerCount - 1,
            isFollowed: false,
          };
        }
      });
    },

    addFollowing(userId) {
      this.users = this.users.map((user) => {
        if (user.id !== userId) {
          return user;
        } else {
          return {
            ...user, // 保留原有資料
            isFollowed: true,
            FollowerCount: user.FollowerCount + 1,
          };
        }
      });
    },
  },
};
</script>
