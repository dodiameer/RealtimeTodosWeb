<script>
    import { todoStore } from './stores.js';
    let title;
    let description;
    function addData() {
        if (title && description) {
            todoStore.set([...$todoStore, {title: title, description: description, complete: false}])
            title = "";
            description = "";
            console.log("Updated!", $todoStore)
        }
    }
</script>

<label for="Task title">
    Task title:<br>
    <input type="text" name="Task title" bind:value={title}>
</label>
<label for="Task description">
    Task description<br>
    <input type="text" name="Task description" bind:value={description}>
</label>
<button on:click={addData}>Add</button>

<style>
    input {
        margin: 0.5em 0 1em 0;
    }
</style>