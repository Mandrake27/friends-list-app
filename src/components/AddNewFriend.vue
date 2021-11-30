<template>
  <form ref="friendForm" @submit.prevent="submitNewFriend">
    <div>
      <label for="name">Name</label>
      <input type="text" v-model="name" id="name">
    </div>
    <div>
      <label for="phone">Phone</label>
      <input type="tel" v-model="phone" id="phone">
    </div>
    <div>
      <label for="email">Email</label>
      <input type="email" v-model="email" id="email">
    </div>
    <div>
      <label for="isFavorite">Favorite</label>
      <input type="checkbox" v-model="isFavorite" id="isFavorite">
    </div>
    <div>
      <button>Submit</button>
    </div>
  </form>
</template>

<script>
export default {
  emits: ['add-new-friend'],
  data() {
    return {
      name: '',
      phone: '',
      email: '',
      isFavorite: false,
    }
  },
  methods: {
    submitNewFriend() {
      const newFriend = {
        name: this.name,
        phone: this.phone,
        email: this.email,
        isFavorite: this.isFavorite,
      };

      this.$emit('add-new-friend', newFriend);
      this.$refs.friendForm.reset();
    },
  },
}
</script>
