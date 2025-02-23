<template>
  <form @submit.prevent="addFriend">
    <h1>Add New Friend</h1>
    <div>
      <label for="name">Name</label>
      <input type="text" id="name" v-model="name" />
    </div>
    <div>
      <label for="phone">Phone</label>
      <input type="text" id="phone" v-model="phone" />
    </div>
    <div>
      <label for="email">Email</label>
      <input type="email" id="email" v-model="email" />
    </div>
    <div :style="{
      display: 'flex',
      justifyContent: 'center',
      alignItems: 'center',
    }">
      <button :disabled="!isValid" >Add Friend</button>
    </div>


  </form>

</template>

<script>
  export default {
    name: 'add-friend',
    emits: ['add-friend'],
    data() {
      return {
        name: '',
        phone: '',
        email: '',
      };
    },
    methods: {
      addFriend() {
        this.$emit('add-friend', {
          name: this.name,
          phone: this.phone,
          email: this.email,
        });
        this.name = '';
        this.phone = '';
        this.email = '';
      },
    },
    computed: {
      isValid() {
        return this.name && this.phone && this.email;
      },
    },


  };

</script>

<style>
  #app input {
    font: inherit;
    padding: 0.15rem;
  }
  #app label {
    font-weight: bold;
    margin-right: 1rem;
    width: 7rem;
    display: inline-block;
  }
  #app form {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    margin: 1rem auto;
    padding: 1rem;
    box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
    border-radius: 10px;
    width: 90%;
    max-width: 40rem;
  }
  #app form div {
    margin: 1rem 0;
    width: 90%;
    max-width: 20rem;
    /* background-color: aqua; */
  }

  button:disabled {
    background-color: #ccc;
    border-color: #ccc;
    box-shadow: none;
    color: #3f3f3f;
    cursor: not-allowed;
  }

</style>