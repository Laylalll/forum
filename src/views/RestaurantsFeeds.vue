<template>
  <div class="container py-5">
    <!-- 使用 NavTabs 元件 -->
    <NavTabs />
    <h1 class="mt-5">最新動態</h1>
    <hr />
    <div class="row">
      <div class="col-md-6">
        <!-- 最新餐廳 NewestRestaurants -->
        <h3>最新餐廳</h3>
        <NewestRestaurants :restaurants="restaurants" />
      </div>
      <div class="col-md-6">
        <!-- 最新評論 NewestComments-->
        <h3>最新評論</h3>
        <NewestComments :comments="comments" />
      </div>
    </div>
  </div>
</template>

<script>
import NavTabs from "./../components/NavTabs.vue";
import NewestRestaurants from "./../components/NewestRestaurants.vue";
import NewestComments from "./../components/NewestComments.vue";

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
    },
    {
      id: 2,
      name: "Dr. Bill Baumbach",
      tel: "1-965-317-0756",
      address: "2132 Gaylord Grove",
      opening_hours: "08:00",
      description:
        "Est et labore quasi consequatur nisi velit eum.\nVeritatis quam aspernatur totam error earum dolores ea.\nAut similique qui qui qui et.\nVoluptas rerum necessitatibus alias rerum alias ad id distinctio.",
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
    },
    {
      id: 5,
      name: "Maida Ankunding",
      tel: "(457) 456-6127 x9673",
      address: "3807 Rylan Loop",
      opening_hours: "08:00",
      description:
        "Soluta sed cum facilis sequi eius a mollitia nihil alias. Consequatur at sit deserunt aspernatur voluptatem occaecati provident. Aut ipsa numquam saepe quod omnis voluptatibus saepe ut. Maiores nobis non quas aut ipsum molestiae. Cupiditate sunt expedita qui culpa debitis adipisci commodi laudantium.",
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
    },
    {
      id: 6,
      name: "Elsa Koss",
      tel: "(750) 464-5592",
      address: "5883 Lehner Stream",
      opening_hours: "08:00",
      description:
        "Sed natus recusandae tempore blanditiis. Sint facilis saepe nihil qui corporis. Necessitatibus laboriosam dolore omnis. Repudiandae laborum ut ratione voluptatibus quia qui qui deleniti.",
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
    },
    {
      id: 7,
      name: "Jasmin Wiza",
      tel: "(689) 286-0825 x594",
      address: "889 Foster Grove",
      opening_hours: "08:00",
      description: "Ut molestiae nobis a numquam enim eveniet officiis optio.",
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
    },
    {
      id: 9,
      name: "Myrna Wuckert",
      tel: "413-157-1997 x191",
      address: "954 Cesar Extensions",
      opening_hours: "08:00",
      description:
        "Earum sit neque. Blanditiis nostrum dignissimos ullam possimus ea est quia laudantium. Corporis adipisci cumque similique optio quaerat ut. Et magnam rem qui dolores molestias eveniet dignissimos.",
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
    },
  ],
  comments: [
    {
      id: 17,
      text: "Vitae iure est neque debitis voluptatem culpa ut architecto enim.",
      UserId: 1,
      RestaurantId: 17,
      createdAt: "2022-04-25T16:40:51.000Z",
      updatedAt: "2022-04-25T16:40:51.000Z",
      User: {
        id: 1,
        name: "root",
        email: "root@example.com",
        password:
          "$2a$10$deyCFaswbP9U87IBskJQHu9wbEbniPZVGU6nh4EAw1IhRtYm92sXu",
        isAdmin: true,
        image: null,
        createdAt: "2022-04-25T16:40:51.000Z",
        updatedAt: "2022-04-25T16:40:51.000Z",
      },
      Restaurant: {
        id: 17,
        name: "Green Lowe",
        tel: "(148) 983-3009 x36409",
        address: "7241 Will Brooks",
        opening_hours: "08:00",
        description: "cum qui non",
        image:
          "https://loremflickr.com/320/240/restaurant,food/?random=29.400781509245387",
        viewCounts: 0,
        createdAt: "2022-04-25T16:40:51.000Z",
        updatedAt: "2022-04-25T16:40:51.000Z",
        CategoryId: 5,
      },
    },
    {
      id: 46,
      text: "Aut ipsam architecto consequatur dolorem sint ducimus aperiam reprehenderit.",
      UserId: 1,
      RestaurantId: 46,
      createdAt: "2022-04-25T16:40:51.000Z",
      updatedAt: "2022-04-25T16:40:51.000Z",
      User: {
        id: 1,
        name: "root",
        email: "root@example.com",
        password:
          "$2a$10$deyCFaswbP9U87IBskJQHu9wbEbniPZVGU6nh4EAw1IhRtYm92sXu",
        isAdmin: true,
        image: null,
        createdAt: "2022-04-25T16:40:51.000Z",
        updatedAt: "2022-04-25T16:40:51.000Z",
      },
      Restaurant: {
        id: 46,
        name: "Cristal Block",
        tel: "1-481-314-6013 x1884",
        address: "20038 Davion Drive",
        opening_hours: "08:00",
        description:
          "Voluptates temporibus aperiam dolores ab fuga ipsa est quibusdam omnis. Suscipit eveniet ad quidem facere quibusdam molestiae. Soluta culpa fuga exercitationem. Architecto ut enim reprehenderit. Neque a minus est.",
        image:
          "https://loremflickr.com/320/240/restaurant,food/?random=12.715071745044781",
        viewCounts: 0,
        createdAt: "2022-04-25T16:40:51.000Z",
        updatedAt: "2022-04-25T16:40:51.000Z",
        CategoryId: 2,
      },
    },
    {
      id: 68,
      text: "Tempore doloremque ipsam labore laborum.",
      UserId: 1,
      RestaurantId: 18,
      createdAt: "2022-04-25T16:40:51.000Z",
      updatedAt: "2022-04-25T16:40:51.000Z",
      User: {
        id: 1,
        name: "root",
        email: "root@example.com",
        password:
          "$2a$10$deyCFaswbP9U87IBskJQHu9wbEbniPZVGU6nh4EAw1IhRtYm92sXu",
        isAdmin: true,
        image: null,
        createdAt: "2022-04-25T16:40:51.000Z",
        updatedAt: "2022-04-25T16:40:51.000Z",
      },
      Restaurant: {
        id: 18,
        name: "Emile Rolfson",
        tel: "036.633.5128",
        address: "1855 Nienow Garden",
        opening_hours: "08:00",
        description: "Hic enim occaecati ab ut facere.",
        image:
          "https://loremflickr.com/320/240/restaurant,food/?random=13.760777996907025",
        viewCounts: 0,
        createdAt: "2022-04-25T16:40:51.000Z",
        updatedAt: "2022-04-25T16:40:51.000Z",
        CategoryId: 3,
      },
    },
    {
      id: 95,
      text: "Dignissimos assumenda corporis voluptatibus animi.",
      UserId: 1,
      RestaurantId: 45,
      createdAt: "2022-04-25T16:40:51.000Z",
      updatedAt: "2022-04-25T16:40:51.000Z",
      User: {
        id: 1,
        name: "root",
        email: "root@example.com",
        password:
          "$2a$10$deyCFaswbP9U87IBskJQHu9wbEbniPZVGU6nh4EAw1IhRtYm92sXu",
        isAdmin: true,
        image: null,
        createdAt: "2022-04-25T16:40:51.000Z",
        updatedAt: "2022-04-25T16:40:51.000Z",
      },
      Restaurant: {
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
      },
    },
    {
      id: 120,
      text: "Eum dolore quo repellat expedita sapiente.",
      UserId: 1,
      RestaurantId: 20,
      createdAt: "2022-04-25T16:40:51.000Z",
      updatedAt: "2022-04-25T16:40:51.000Z",
      User: {
        id: 1,
        name: "root",
        email: "root@example.com",
        password:
          "$2a$10$deyCFaswbP9U87IBskJQHu9wbEbniPZVGU6nh4EAw1IhRtYm92sXu",
        isAdmin: true,
        image: null,
        createdAt: "2022-04-25T16:40:51.000Z",
        updatedAt: "2022-04-25T16:40:51.000Z",
      },
      Restaurant: {
        id: 20,
        name: "Katelyn Zulauf",
        tel: "(938) 483-2004",
        address: "906 Lavada Estates",
        opening_hours: "08:00",
        description:
          "Corporis deleniti omnis.\nFacilis neque dignissimos quaerat laudantium.",
        image:
          "https://loremflickr.com/320/240/restaurant,food/?random=56.50451494979105",
        viewCounts: 0,
        createdAt: "2022-04-25T16:40:51.000Z",
        updatedAt: "2022-04-25T16:40:51.000Z",
        CategoryId: 5,
      },
    },
    {
      id: 145,
      text: "Veritatis nam provident qui enim dolore id voluptates delectus qui.",
      UserId: 1,
      RestaurantId: 45,
      createdAt: "2022-04-25T16:40:51.000Z",
      updatedAt: "2022-04-25T16:40:51.000Z",
      User: {
        id: 1,
        name: "root",
        email: "root@example.com",
        password:
          "$2a$10$deyCFaswbP9U87IBskJQHu9wbEbniPZVGU6nh4EAw1IhRtYm92sXu",
        isAdmin: true,
        image: null,
        createdAt: "2022-04-25T16:40:51.000Z",
        updatedAt: "2022-04-25T16:40:51.000Z",
      },
      Restaurant: {
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
      },
    },
    {
      id: 12,
      text: "Ut tenetur odio vel aliquam earum omnis laudantium dolores.",
      UserId: 2,
      RestaurantId: 12,
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
      Restaurant: {
        id: 12,
        name: "Cassidy Blick",
        tel: "(685) 907-2356",
        address: "30002 Rachel Shoal",
        opening_hours: "08:00",
        description: "et",
        image:
          "https://loremflickr.com/320/240/restaurant,food/?random=74.45100128410873",
        viewCounts: 0,
        createdAt: "2022-04-25T16:40:51.000Z",
        updatedAt: "2022-04-25T16:40:51.000Z",
        CategoryId: 3,
      },
    },
    {
      id: 52,
      text: "Molestiae minima rerum sit consequatur harum.",
      UserId: 2,
      RestaurantId: 2,
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
      Restaurant: {
        id: 2,
        name: "Dr. Bill Baumbach",
        tel: "1-965-317-0756",
        address: "2132 Gaylord Grove",
        opening_hours: "08:00",
        description:
          "Est et labore quasi consequatur nisi velit eum.\nVeritatis quam aspernatur totam error earum dolores ea.\nAut similique qui qui qui et.\nVoluptas rerum necessitatibus alias rerum alias ad id distinctio.",
        image:
          "https://loremflickr.com/320/240/restaurant,food/?random=13.967577181543156",
        viewCounts: 0,
        createdAt: "2022-04-25T16:40:51.000Z",
        updatedAt: "2022-04-25T16:40:51.000Z",
        CategoryId: 3,
      },
    },
    {
      id: 77,
      text: "Inventore aut ducimus.",
      UserId: 2,
      RestaurantId: 27,
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
      Restaurant: {
        id: 27,
        name: "Cathryn Pacocha",
        tel: "136.165.6708",
        address: "14924 Rhiannon Glen",
        opening_hours: "08:00",
        description:
          "Animi eius officia vero rerum soluta eius sequi ducimus et. Atque molestiae tempore est et.",
        image:
          "https://loremflickr.com/320/240/restaurant,food/?random=73.01556130491218",
        viewCounts: 0,
        createdAt: "2022-04-25T16:40:51.000Z",
        updatedAt: "2022-04-25T16:40:51.000Z",
        CategoryId: 1,
      },
    },
    {
      id: 99,
      text: "Error aspernatur quia nam in necessitatibus eos.",
      UserId: 2,
      RestaurantId: 49,
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
      Restaurant: {
        id: 49,
        name: "Prince Barton MD",
        tel: "428-737-2678",
        address: "98440 Franecki Green",
        opening_hours: "08:00",
        description:
          "Dolores doloremque suscipit corrupti facere ipsum. Iusto illo magni labore porro qui dolores sunt quo. Odit labore est sequi. Qui cumque et et unde et et harum nihil.",
        image:
          "https://loremflickr.com/320/240/restaurant,food/?random=90.71733084189357",
        viewCounts: 0,
        createdAt: "2022-04-25T16:40:51.000Z",
        updatedAt: "2022-04-25T16:40:51.000Z",
        CategoryId: 4,
      },
    },
  ],
};

export default {
  components: {
    NavTabs, // NavTabs: NavTabs的縮寫
    NewestRestaurants, // NewestRestaurants: NewestRestaurants
    NewestComments, // NewestComments: NewestComments
  },
  // Vue 會在沒有資料時使用此預設值
  data() {
    return {
      restaurants: [],
      comments: [],
    };
  },

  methods: {
    // 載入資料
    fetchFeeds() {
      this.restaurants = dummyData.restaurants;
      this.comments = dummyData.comments.filter(
        (comment) => comment.Restaurant && comment.text //若Restaurant跟text存在的話 回傳，篩掉null
      );
    },
  },

  // 掛載事件
  created() {
    console.log("feeds created");
    this.fetchFeeds();
  },
};
</script>
