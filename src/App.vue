<template>
  <header>
    <h1>Friends List</h1>
  </header>
  <section>
    <add-friend @add-friend="processFriend" />
  </section>
  <section>
    <ul>
      <friend-contact 
        v-for="friend in friends" 
        :key="friend.idx" 
        v-bind="friend"
        @toggle-favorite="toggleFavorite"
        @remove-friend="removeFriend"
      />
    </ul>
  </section>
</template>

<script>
import FriendContact from "./components/FriendContact.vue";
import AddFriend from "./components/AddFriend.vue";

export default {
  name: "App",
  components: {
    FriendContact,
    AddFriend,
  },
  data() {
    return {
      friends: [
        {
          idx: "manuel",
          name: "Manuel Lorenz",
          phone: "01234 5678 991",
          email: "manuel@localhost.com",
          isFavorite: false,
        },
        {
          idx: "julie",
          name: "Julie Jones",
          phone: "09876 543 221",
          email: "julie@localhost.com",
          isFavorite: false,
        },
      ],
    };
  },
  methods: {
    toggleFavorite(friendId) {
      this.friends = this.friends.map(
        (friend) =>
          friend.idx === friendId ? { ...friend, isFavorite: !friend.isFavorite } : friend
      );
    },
    processFriend(friend) {
      this.friends.unshift({
        idx: new Date().toISOString(),
        ...friend,
        isFavorite: false,
      });
    },
    removeFriend(friendId) {
      this.friends = this.friends.filter((friend) => friend.idx !== friendId);
    },
  },
};
</script>

<style>

@import url('https://fonts.googleapis.com/css2?family=Jost&display=swap');

* {
  box-sizing: border-box;
}

html {
  font-family: "Jost", sans-serif;
}

body {
  margin: 0;
}

header {
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  margin: 3rem auto;
  border-radius: 10px;
  padding: 1rem;
  background-color: #58004d;
  color: white;
  text-align: center;
  width: 90%;
  max-width: 40rem;
}

ul {
  margin: 0;
  padding: 0;
  list-style: none;
}

</style>
