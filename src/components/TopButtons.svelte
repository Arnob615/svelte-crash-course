<script>
    import { tasks } from '../store';
    export let showForm = false;
    export let showList = true;
    export let filter = 'all';

    const changeFilter = (filterName) => {
        filter = filterName;
    }

    const clearTask = () => {
        const tempTasks = $tasks.filter(t => !t.completed);
        tasks.set(tempTasks);
    }
</script>

<div>
    <button class="btn btn-primary btn-sm" on:click={() => showForm = !showForm}>Create</button>
    <button class="btn btn-success btn-sm" on:click={() => showList = !showList}> {showList ? 'Hide' : 'Show'} </button>
    <button class="btn btn-info btn-sm" on:click={() => changeFilter('all')}>All</button>
    <button class="btn btn-info btn-sm" on:click={() => changeFilter('active')}>Active</button>
    <button class="btn btn-info btn-sm" on:click={() => changeFilter('completed')}>Completed</button>
    <button class="btn btn-danger btn-sm" on:click={clearTask}>Clear</button>
</div>