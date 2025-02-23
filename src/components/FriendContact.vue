<template>
  <li>
    <h2>{{ name }}{{ isFavorite ? ' (favorited)' : '' }}</h2>
    <p><button @click="toggleDetails">{{ toggleText() }}</button></p>
    <p><button @click="removeFriend">Unfriend</button></p>
    <p><button @click="toggleFavorite">Toggle Favorite</button></p>
    <ul v-if="detailsAreVisible">
      <li><strong>Phone:</strong> {{ phone }}</li>
      <li><strong>Email:</strong> {{ email }}</li>
    </ul>
  </li>
</template>
<script>
  export default {
    name: 'friend-contact',
    props: {
      idx: String,
      name: String,
      phone: String,
      email: String,
      isFavorite: Boolean,
    },
    emits: {
      'toggle-favorite': function(friendId) {
        if (typeof friendId === 'string') {
          return true;
        }
        return false;
      },
      'remove-friend': function(friendId) {
        if (typeof friendId === 'string') {
          return true;
        }
        return false;
      },
    },
    data () {
      return {
        detailsAreVisible: false,
      };
    },
    methods: {
      toggleDetails() {
        this.detailsAreVisible = !this.detailsAreVisible;
      },
      toggleText() {
        return this.detailsAreVisible ? 'Hide Details' : 'Show Details';
      },
      toggleFavorite() {
        this.$emit('toggle-favorite', this.idx);
      },
      removeFriend() {
        this.$emit('remove-friend', this.idx);
      },
    },
  }
</script>
<style>

  ul {
    margin: 0;
    padding: 0;
    list-style: none;
  }

  li {
    box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
    margin: 1rem auto;
    border-radius: 10px;
    padding: 1rem;
    text-align: center;
    width: 90%;
    max-width: 40rem;
  }

  h2 {
    font-size: 2rem;
    border-bottom: 4px solid #ccc;
    color: #58004d;
    margin: 0 0 1rem 0;
  }

  button {
    font: inherit;
    cursor: pointer;
    border: 1px solid #ff0077;
    background-color: #ff0077;
    color: white;
    padding: 0.05rem 1rem;
    box-shadow: 1px 1px 2px rgba(0, 0, 0, 0.26);
  }

  button:hover,
  button:active {
    background-color: #ec3169;
    border-color: #ec3169;
    box-shadow: 1px 1px 4px rgba(0, 0, 0, 0.26);
  }

</style>