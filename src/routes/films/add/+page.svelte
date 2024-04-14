<script>
    import { goto } from '$app/navigation';


  import { FilmStore } from "../../../film-store";

    let name = '';
    let director = '';

    // handlesubmit function
    let handleSubmit = () => {
        FilmStore.update(prev => {
            // variable for id ~ index into film
            let id = prev[prev.length-1].id +1

            let newFilm = {id: id, name: name, director: director}
            return [...prev, newFilm]
        })

        goto('/films/')
    }
</script>

<div>

    <h2 class="my-4">Add a Film</h2>

    <div class="col-12 col-md-6">
        <form on:submit|preventDefault={handleSubmit}>
            <div class="mb-3">
                <input class="form-control" type="text" placeholder="name" bind:value={name}/>
            </div>
            <div class="mb-3">
                <input class="form-control" type="text" placeholder="director" bind:value={director}/>
            </div>
        
            <button class="btn btn-primary" type="submit">Submit</button>
        </form>
    </div>

</div>

<!-- unneeded now -->
<!-- <style>
    .submit {
        background-color: blue;
        color: white;
        padding: 5px;
        border-radius: 10%;
        cursor: pointer;
        margin-top: 10px;
    }

    .submit:hover {
        transform: scale(110%);
    }
</style> -->