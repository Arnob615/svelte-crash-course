<script>
    let colors = ['orange', 'red', 'yellow', 'blue', 'purple', 'green']

    export let selectedColor = 'orange';

    const changeColor = (color) => {
        selectedColor = color;
    }
</script>

<style>
    .color {
        width: 50px;
        height: 50px;
        border-radius: 50%;
    }

    .selected {
        border: 2px solid black;
    }
</style>

<div class="d-flex">
    {#each colors as color}
        <div class="color mx-2 {selectedColor === color ? 'selected' : ''}" style="background: {color}" on:click={() => changeColor(color)}>
        </div>
    {/each}
</div>