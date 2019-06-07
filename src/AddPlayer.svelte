<script>
    import { createEventDispatcher } from 'svelte';

    const dispatch = createEventDispatcher();

    let player = {
        name: "",
        points: 0
    }

    const onSubmit = (e) => {
        if (e.srcElement.name.value !== "") {
            e.preventDefault();
            dispatch("addplayer", player);
            player = {
                name: "",
                points: 0
            }
        }
    }
</script>

<form class="grid-3" on:submit={onSubmit}>
    <input type="text" id="name" placeholder="Player Name" bind:value={player.name}>
    <input type="number" placeholder="Player Points" bind:value={player.points}>
    <input type="submit" class="btn btn-primary" value="Add Player">
</form>