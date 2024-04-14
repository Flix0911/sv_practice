<script>
    import { FilmStore } from '../../../film-store'


    export let data;

    let film = $FilmStore.find(film => film.id == data.id)
    console.log(film)
</script>

<!-- if statement -->
{#if film}
    <p>{film.name}, directed by: {film.director}</p>
{:else}
    <p>No film was found with id {film.id}</p>
{/if}