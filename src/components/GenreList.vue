<template>
  <div class="genre-list">
    <GenreCard
      v-for="genre in genres"
      :key="genre.id"
      :genre="genre"
    />
  </div>
</template>

<script>
import { mapState, mapActions } from 'vuex';
import GenreCard from "@/components/GenreCard.vue";

// Bud -- I was trying to use mapState here, but it wasn't working...
// Any ideas? Computed seems like the wrong way to do this
export default {
  components: {
    GenreCard,
  },
  computed: {
    ...mapState('genre', ['genres']),
  },
  mounted() {
    this.fetchGenres();
  },
  methods: {
    ...mapActions('genre', ['fetchGenres']),
  },
};
</script>

<style lang="css" scoped>
.genre-list {
  padding: 0 15%;
}
</style>
