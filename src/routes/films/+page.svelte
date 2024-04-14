<script>
    import { FilmStore } from '../../film-store'

    // can remove and add a hook
    // let films = []

    // const unsubscribe = FilmStore.subscribe(values => films = values)

    // onDestroy(unsubscribe)
</script>

<!-- if statement -->
<!-- {#if film.startsWith('F')}
    <p>Starts with 'T''</p>
{:else }
    <p>Doesn't start with 'T'</p>
{/if} -->

<!-- define UL -->
<ul>
    {#each $FilmStore as film}
        <li>
            <a href="films/{film.id}">{film.name}
        </li>

    {/each}
</ul>
