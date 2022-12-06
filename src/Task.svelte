<script lang='ts'>
    import { tasksArray } from "./stores";
	import type { TaskType } from "./types/tasktype.type";
    
    export let task: TaskType
 
    let done: boolean = false

    const finishTask = (event: MouseEvent) => {
        done = !done
    }

    const deleteTask = (event: MouseEvent) => {
        $tasksArray = $tasksArray.filter((el: TaskType) => el.value !== task.value)
    }

</script>

<div class='grid xl:grid-cols-12 lg:grid-cols-6 sm:grid-cols-4 rounded px-6 py-6 min-h-fit justify-items-stretch'>
    <div class={`col-span-4 text-dark-blue justify-self-start`}>
        <p class={`${done === true ? `line-through` : ''}`}>
            {task.value}
        </p>
    </div>
    <div class='col-span-2 text-dark-blue justify-self-end'>
    <p class={`${done === true ? `line-through` : ''}`}>
        {task.user}
        </p>
    </div>
    <div class='col-span-4 sm:col text-dark-blue justify-self-start'>
     <p class={`${done === true ? `line-through` : ''}`}>
        {task.date}
    </p>
    </div>
    <button on:click={deleteTask} class='col-span-1 text-dark-blue justify-self-end'>
        <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-6 h-6">
            <path stroke-linecap="round" stroke-linejoin="round" d="M14.74 9l-.346 9m-4.788 0L9.26 9m9.968-3.21c.342.052.682.107 1.022.166m-1.022-.165L18.16 19.673a2.25 2.25 0 01-2.244 2.077H8.084a2.25 2.25 0 01-2.244-2.077L4.772 5.79m14.456 0a48.108 48.108 0 00-3.478-.397m-12 .562c.34-.059.68-.114 1.022-.165m0 0a48.11 48.11 0 013.478-.397m7.5 0v-.916c0-1.18-.91-2.164-2.09-2.201a51.964 51.964 0 00-3.32 0c-1.18.037-2.09 1.022-2.09 2.201v.916m7.5 0a48.667 48.667 0 00-7.5 0" />
        </svg>
    </button>
    <button on:click={finishTask} type='button' class='col-span-1 text-dark-blue justify-self-end'>
        <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-6 h-6">
            <path stroke-linecap="round" stroke-linejoin="round" d="M10.125 2.25h-4.5c-.621 0-1.125.504-1.125 1.125v17.25c0 .621.504 1.125 1.125 1.125h12.75c.621 0 1.125-.504 1.125-1.125v-9M10.125 2.25h.375a9 9 0 019 9v.375M10.125 2.25A3.375 3.375 0 0113.5 5.625v1.5c0 .621.504 1.125 1.125 1.125h1.5a3.375 3.375 0 013.375 3.375M9 15l2.25 2.25L15 12" />
    </svg>
    </button>
</div>