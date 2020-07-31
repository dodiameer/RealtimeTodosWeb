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

<input type="text" bind:value={title}>
<input type="text" bind:value={description}>
<button on:click={addData}>Add</button>