<script>
    import { FilmStore } from '../../film-store'
    import { onMount } from 'svelte';

    onMount(async function () {
    if(!$FilmStore.length) {
        const endpoint = 'http://localhost:8000/api/films/'

        const response = await fetch(endpoint)

        const data = await response.json()
        FilmStore.set(data)
    }

        // console.log(data)
    })

    // handleclick event ~ unneeded now
    // let handleClick = () => FilmStore.update(prev => {
    //     let newFilm = {id: 3, name: 'Drive', director: 'Nicholas Winding Refn'}
    //     return [...prev, newFilm]
    // })

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
<div>
    <h2 class="my-4">Film List</h2>
    
    <div class="my-4 row">
        {#each $FilmStore as film}
        <div class="col-12 col-sm-6 col-md-4">
            
            <div class="card w-100 h-100">
                <img class="card-img-top" style="height: 300px; object-fit: cover" 
                    src="{film.image}" 
                    alt="Film">
                <div class="card-body d-flex flex-column justify-content-between gap-4">
					<div>
                        <h5 class="card-title">{ film.name }</h5>
                        <p class="card-text">Directed by { film.director }</p>
                    </div>
                    <div>
                        <a href="/films/{film.id}" class="btn btn-primary">View</a>
					</div>
                </div>
              </div>

        </div>
        {/each}
    </div>
    
</div>