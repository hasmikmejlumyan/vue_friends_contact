<template>
  <li>
    <h2>{{ name }} {{ isFavorite ? '(Favorite)' : '' }} </h2>
    <button @click="toggleFavorite">Toggle Favorite</button>
    <button @click="toggleDetails">Show Details</button>
    <ul v-if="detailsAreVisible">
      <li><strong>Phone</strong> {{ phoneNumber }} </li>
      <li><strong>Email</strong> {{ emailAddress }} </li>
    </ul>
  </li>

  <button @click="$emit('delete', id)">Delete</button>
</template>

<script>
export default {
  // props: [
  //   'name',
  //   'phoneNumber',
  //   'emailAddress',
  //   'isFavorite',
  // ],

  props: {
    id: {
      type: String,
      required: true
    },
    name: {
      type: String,
      required: true,
    },
    phoneNumber: {
      type: String,
      required: true,
    },
    emailAddress: {
      type: String,
      required: true,
    },
    isFavorite: {
      type: Boolean,
      required: false,
      default: false,
      // validator: (value) => {
      //   return value === '1' || value === '0';
      // }
    },
  },

  emits: ['toggle-favorite', 'delete'],
  // emits: {
  //   'toggle-favorite': (id) => {
  //     if (id) {
  //       return true;
  //     } else {
  //       console.warn('Id Is missing!');
  //       return false;
  //     }
  //   }
  // },

  data() {
    return {
      detailsAreVisible: false,
    };
  },

  methods: {
    toggleDetails() {
      this.detailsAreVisible = !this.detailsAreVisible;
    },
    toggleFavorite() {
      this.$emit('toggle-favorite', this.id);
    },
  }
}
</script>

<style></style>