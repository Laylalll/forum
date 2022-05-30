<template>
  <ul class="nav nav-tabs mb-4">
    <li v-for="tab in tabs" :key="tab.id" class="nav-item">
      <router-link :to="tab.path" class="nav-link">
        {{ tab.title }}
      </router-link>
    </li>
  </ul>
</template>

<script>
import { v4 as uuidv4 } from "uuid";
export default {
  data() {
    return {
      tabs: [
        {
          id: uuidv4(),
          path: "/restaurants",
          title: "首頁",
        },
        {
          id: uuidv4(),
          path: "/restaurants/feeds",
          title: "最新動態",
        },
        {
          id: uuidv4(),
          path: "/restaurants/top",
          title: "TOP 10 人氣餐廳",
        },
        {
          id: uuidv4(),
          path: "/users/top",
          title: "美食達人",
        },
      ],
    };
  },
};
</script>
