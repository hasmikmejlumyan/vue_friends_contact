<template>
  <section>
    <header>
      <h2>My Frineds</h2>
    </header>
    <new-friend @add-contact="addContact"></new-friend>
    <ul>
      <li>
        <friend-contact
          v-for="friend in friends"
          :key="friend.id"
          :id="friend.id"
          :name="friend.name"
          :phone-number="friend.phone"
          :email-address="friend.email"
          :is-favorite="friend.isFavorite"
          @toggle-favorite="toggleFavoriteStatus"
          @delete="deleteContact"
        ></friend-contact>
      </li>
    </ul>
  </section>
</template>
<script>
export default {
  data() {
    return {
      friends: [
        {
          id: 'manuel',
          name: 'Manuel Lorenz',
          phone: '0102030405',
          email: 'manuel@example.com',
          isFavorite: true,
        },
        {
          id: 'julie',
          name: 'Julie Jones',
          phone: '01452424405',
          email: 'julie@example.com',
          isFavorite: false,
        }
      ]
    }
  },

  methods: {
    toggleFavoriteStatus(friendId) {
      const identifiedFriend = this.friends.find(friend => friend.id === friendId);
      identifiedFriend.isFavorite = !identifiedFriend.isFavorite;
    },

    addContact(name, phone, email) {
      const newFriendContact = {
        id: new Date().toISOString(),
        name: name,
        phone: phone,
        email: email,
        isFavorite: false,
      };

      this.friends.push(newFriendContact);
    },

    deleteContact(friendId) {
      this.friends = this.friends.filter(friend => friend.id !== friendId);
    },
  }
}
</script>

<style>
 header {
   box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
 }
</style>