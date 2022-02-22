<script content='module'>
	import CreateTask from "./components/CreateTask.svelte";
	import Tasks from "./components/Tasks.svelte";
	import TopButtons from "./components/TopButtons.svelte";
	import { tasks } from './Store';

	$: console.log($tasks)

	let toggleCreateTaskForm = false;
	let toggleTaskList = true;
	let filter = 'all';

	$: console.log(filter)

	$: activeTasks = $tasks.filter(t => !t.completed);
	$: completedTasks = $tasks.filter(t => t.completed);

</script>

<svelte:head>
	<link href="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-1BmE4kWBq78iYhFldvKuhfTAU6auU8tT94WrHftjDbrCEXSU1oBoqyl2QvZ6jIW3" crossorigin="anonymous">
	<title>Svelte Crash Course</title>
</svelte:head>

<div class="container">
	<div class="row">
		<div class="col-md-6 offset-md-2 my-4">
			<h1 class="text-center text-info">Hello Svelte</h1>
			<TopButtons 
				bind:showForm={toggleCreateTaskForm} 
				bind:showList={toggleTaskList} 
				bind:filter={filter}/>

			{#if toggleCreateTaskForm}
				<CreateTask />
			{/if}

			{#if toggleTaskList}
				{#if filter === 'all'}
					<Tasks taskList={$tasks} label ={'ALL'} />
				{:else if filter === 'active'}
					<Tasks taskList={activeTasks} label ={'Active'} />
				{:else if filter === 'completed'}
					<Tasks taskList={completedTasks} label ={'Completed'} />
				{/if}
			{/if}

		</div>
	</div>
</div>