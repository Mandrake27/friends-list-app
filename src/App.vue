<template>
  <header><h1>My Friends</h1></header>
  <add-new-friend @add-new-friend="addNewFriend"/>
  <ul>
      <friend-contact
          v-for="{ id, name, phone, email, isFavorite } in friends"
          :key="id"
          :id="id"
          :name="name"
          :phone-number="phone"
          :email-address="email"
          :is-favorite="isFavorite"
          @toggle-favorite="toggleFavoriteStatus"
          @delete-friend="deleteFriend"
      />
  </ul>
</template>

<script>
import FriendContact from "@/components/FriendContact";
import AddNewFriend from "@/components/AddNewFriend";

export default {
  components: {
    FriendContact,
    AddNewFriend,
  },
  data() {
    return {
      friends: [
        {
          id: 1,
          name: 'Igor Torreto',
          phone: '0123 456 789',
          email: 'torreto@gmail.com',
          isFavorite: true,
        },
        {
          id: 2,
          name: 'Anya Bekmansurova',
          phone: '0987 654 321',
          email: 'bekmansurova@gmail.com',
          isFavorite: true,
        }
      ],
    }
  },
  methods: {
    toggleFavoriteStatus(friendId) {
      const neededFriend = this.friends.find(({ id }) => id === friendId);
      neededFriend.isFavorite = !neededFriend.isFavorite;
    },
    addNewFriend(newFriend) {
      newFriend.id = this.friends.at(-1) + 1;
      this.friends.push(newFriend);
    },
    deleteFriend(friendId) {
      this.friends = this.friends.filter(({ id }) => id !== friendId);
    }
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Jost&display=swap');
* {
  box-sizing: border-box;
}

html {
  font-family: 'Jost', sans-serif;
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

#app ul {
  margin: 0;
  padding: 0;
  list-style: none;
}

#app li,
#app form {
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  margin: 1rem auto;
  border-radius: 10px;
  padding: 1rem;
  text-align: center;
  width: 90%;
  max-width: 40rem;
}

#app h2 {
  font-size: 2rem;
  border-bottom: 4px solid #ccc;
  color: #58004d;
  margin: 0 0 1rem 0;
}

#app button {
  font: inherit;
  cursor: pointer;
  border: 1px solid #ff0077;
  background-color: #ff0077;
  color: white;
  padding: 0.05rem 1rem;
  box-shadow: 1px 1px 2px rgba(0, 0, 0, 0.26);
}

#app button:hover,
#app button:active {
  background-color: #ec3169;
  border-color: #ec3169;
  box-shadow: 1px 1px 4px rgba(0, 0, 0, 0.26);
}

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
#app form div {
  margin: 1rem 0;
}

</style>
