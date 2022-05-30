<template>
  <!-- User Profile Card -->
  <div class="card mb-3">
    <div class="row no-gutters">
      <div class="col-md-4">
        <img :src="user.image" width="300px" height="300px" />
      </div>
      <div class="col-md-8">
        <div class="card-body">
          <h5 class="card-title">{{ user.name }}</h5>
          <p class="card-text">{{ user.email }}</p>
          <ul class="list-unstyled list-inline">
            <li>
              <strong>{{ user.commentsLength }}</strong> 已評論餐廳
            </li>
            <li>
              <strong>{{ user.favoritedRestaurantsLength }}</strong>
              收藏的餐廳
            </li>
            <li>
              <strong>{{ user.followingsLength }}</strong> followings (追蹤者)
            </li>
            <li>
              <strong>{{ user.followersLength }}</strong> followers (追隨者)
            </li>
          </ul>
          <p v-if="currentUser.id === user.id">
            <a href="/users/2/edit"
              ><button type="submit" class="btn btn-primary">edit</button></a
            >
          </p>
          <p v-else>
            <button
              v-if="isFollowed"
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
  </div>
</template>

<script>
const dummyUser = {
  currentUser: {
    id: 1,
    name: "管理者",
    email: "root@example.com",
    image: "https://i.pravatar.cc/300",
    isAdmin: true,
  },
  isAuthenticated: true,
};

export default {
  props: {
    user: {
      type: Object,
      required: true,
    },
    initialIsFollowed: {
      type: Boolean,
      required: true,
    },
  },

  data() {
    return {
      isFollowed: this.initialIsFollowed,
      currentUser: dummyUser.currentUser, //建立暫時用的登入使用者資訊 dummyUser
    };
  },

  methods: {
    deleteFollowing(userId) {
      this.isFollowed = false;
    },

    addFollowing(userId) {
      this.isFollowed = true;
    },
  },
};
</script>