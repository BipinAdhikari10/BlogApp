<template>
  <div>
    <UserList :users="users" />
  </div>
</template>

<script>
import UserList from "../components/UserList.vue";
import axios from "axios";
export default {
  name: "HomePage",
  components: {
    UserList,
  },
  data() {
    return {
      message: "This is home component",
      users: [
        {
          id: "u1",
          name: "Bipin Adhikari",
          image:
            "https://encrypted-tbn1.gstatic.com/licensed-image?q=tbn:ANd9GcSAHmDSOdLA5YgFlEkMmgdweIf3jyGI0EGKqU5U7TpO70GFAY48v1N51eMRpY6mbG-VzfPvgObhOwB8lX4",
          places: 5,
        },
        {
          id: "u2",
          name: "Debaki Upreti",
          image:
            "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQYQyYFufwV60a-zpTYR6TJu5VHJ6b8r2x8tg&s",
          places: 4,
        },
      ],
    };
  },
  props: {},
  methods: {
    getUserData() {
      axios
        .get("http://localhost:5000/users")
        .then((response) => {
          console.log(response.data);
          return response.data; 
        })
        .catch((error) => {
          console.error("Error fetching user data:", error);
        });
    },
  },
  created() {
    this.getUserData();
  },
};
</script>

<style></style>
