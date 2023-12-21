<script>
	import { Checkbox } from '$lib/components/ui/checkbox';
	import { Label } from '$lib/components/ui/label';
	import { ChevronRight, PlusIcon, X } from 'lucide-svelte';
	import { Button } from '$lib/components/ui/button';
	import { Plus } from 'lucide-svelte';
	import { Input } from '$lib/components/ui/input';
	import { list } from 'postcss';

	let checked = false;
	let todos = [];
	let todoValue = '';
    
	function addToList() {
        todos = [...todos, todoValue] 
        todoValue = "";
	}

    function removeFromList(indexToDelete) {
        todos = todos.map((value, index) => {
            // if index passed in is not equal to the index of the current item
            return index !== indexToDelete;
        });
    }

	// $: console.log({todos});
</script>

<h1>My ToDo List</h1>
<form class="flex w-full max-w-sm items-center space-x-2">
	<Input bind:value={todoValue} type="List" placeholder="Add todo item" />
	<Button variant="outline" size="icon" on:click={addToList}>
		<PlusIcon className="h-4 w-4" />
	</Button>
</form>

 <div>
    {#each todos as todo, index (index)}
        <div class="flex items-center space-x-4">
            <Label
                id="terms-label"
                for="terms"
                class="text-sm font-medium leading-none peer-disabled:cursor-not-allowed peer-disabled:opacity-70"
            >
                {todo}
            </Label>
            <button on:click={() => removeFromList(index)}>
                <X className="h-4 w-4" />
                </button>
        </div>
    {/each}
</div>
 

<!-- 
{#each [todos}] as item}
    <h1>{item}</h1>
{/each} -->