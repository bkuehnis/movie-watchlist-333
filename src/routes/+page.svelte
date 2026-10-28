<script>
  import MovieCard from "$lib/components/MovieCard.svelte";
    import { get } from "svelte/store";
  let { data } = $props();

  let filterByWatchlist = $state(false);

  let movies = $derived.by( () => {
    if (filterByWatchlist) {
      let filteredMovies = data.movies.filter( m =>  m.watchlist)
      return filteredMovies;
    }
    return data.movies;
  })
  let movie = movies[0];

</script>

<h1>Welcome to ScreenStack, Week 6</h1>
<p>Your tracker and search engine for movies and tv shows</p>

    <div class="col-sm-6 col-md-4 col-lg-3 mb-2 gx-2">
      <MovieCard {movie}></MovieCard>
    </div>
