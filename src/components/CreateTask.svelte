<script>
    import { tasks } from '../Store';
    import Color from './Color.svelte';

    let title = '';
    let description = '';
    let color = '';

    const handleSubmitForm = (e) => {
        if (!title) {
            alert('Please Provide a title')
            return
        }

        let id = (Math.random() * new Date().getTime()).toString();

        const task = {
            id,
            title,
            description,
            color,
            completed: false,
            editable: false
        }
        const newTasks = [task, ...$tasks]
        tasks.set(newTasks)

        e.target.reset();
    }
</script>

<div class="card card-body my-4">
    <form on:submit|preventDefault={handleSubmitForm}>
        <div class="form-group">
            <label for="title"> Enter A Task Title </label>
            <input type="text" placeholder="Task Title" id="title" class="form-control" bind:value={title}>
        </div>

        <div class="form-group">
            <label for="desc"> Enter A Short Description </label> <br>
            <textarea name="form-control" id="desc" cols="58" rows="5" bind:value={description}></textarea>
        </div>

        <Color bind:selectedColor={color}/>
        
        <input type="submit" class="btn btn-primary my-4" value="Create Task">
    </form>
</div>