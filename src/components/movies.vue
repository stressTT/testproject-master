<template>
  <div>
    <div v-for="movie of movies" :key="movie.id">
        <p @click='$router.push({name:"Movie", params:{id:movie.id}})'>{{movie.name}}</p>
        
    </div>
  </div>
</template>

<script>
export default {
  name: "movies",
  data() {
    return {
      errors: [],
      movies: [],
      urlMovie: "http://localhost:3001/movies",
    };
  },
  
  async mounted() {
    try {
      const takeData = await fetch(this.urlMovie);
      const result = await takeData.json();
      this.movies.push(...result);
      console.log(this.movies);
    } catch (error) {
      this.errors.push(error);
    }
  },
};
</script>