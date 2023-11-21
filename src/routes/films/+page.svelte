<script>
    let film = 'The Godfather'

    import {FilmStore} from '../../film-store'
    import {onDestroy} from 'svelte'

    let films = [
        // {id: 1, name: 'the godfather', director: 'francis ford coppola'},
        // {id: 2, name: 'the showshank', director: 'molu'}
    ]

    const unsubscribe = FilmStore.subscribe(values => films = values)
    
    onDestroy(unsubscribe)
</script>

{#if film.startsWith('T')}
    <p>start t</p>
{:else}
    <p>dosen't t</p>
{/if}

<h1>{film}</h1>
<style>
    h1{
        font-size:40px;
        background-color: aquamarine;
    }
</style>

<ul>

    {#each $FilmStore as film}
        <li>
            <a href="films/{film.id}">{film.name}</a>
        </li>
    {/each}
</ul>