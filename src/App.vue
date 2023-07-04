<template>
  <section>
    <header>
      <h2>My Frineds</h2>
    </header>
    <ul>
      <li>
        <friend-contact
          v-for="friend in friends"
          :key="friend.id"
          :name="friend.name"
          :phone-number="friend.phone"
          :email-address="friend.email"
          :is-favorite="true"
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
        },
        {
          id: 'julie',
          name: 'Julie Jones',
          phone: '01452424405',
          email: 'julie@example.com',
        }
      ]
    }
  }
}
</script>

<style>
 header {
   box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
 }
</style>