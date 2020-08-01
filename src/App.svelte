<script lang="ts">
    import { onDestroy } from 'svelte'; // For destroying active subscription
    import { todoStore } from "./stores"; // Used for todos
    import Todo from "./Todo.svelte"; // Display component
    import TodoPusher from "./TodoPusher.svelte"; // Todo addition
    
    // Initial empty list filled after subscribing to todoStore
    let todoList = [];
    
    // BEGIN Todo list "boilerplate"
    let todoListUnsub = todoStore.subscribe(val => todoList = val);
    onDestroy(() => todoListUnsub());
    // END Todo list "boilerplate"

</script>

<main>
    <h1>Realtime Todos</h1>
    <ul>
	{#each todoList as todo, idx}
        <Todo 
            title={todo.title} 
            description={todo.description} 
            complete={todo.complete}
            index={idx}
        />
    {:else}
    <h2>No tasks added. Add one below!</h2>
    {/each}
    </ul>
    <TodoPusher/>
</main>

<style>
	h1 {
		font-size: 3em;
		font-weight: 100;
	}
    ul {
        padding: 0;
    }
    main {
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
    }
</style>