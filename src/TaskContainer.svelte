<script lang='ts'>
    import Task from "./Task.svelte";
    export let tasks: TaskType[]
    type TaskType ={
    value: string
    date: string
    user: string
  }
</script>

<div class='grid lg:grid-cols-4 grid-cols-1 gap-2.5 mt-5 px-6 py-6 w-screen h-fit-content bg-blue-gray justify-items-center'>
    {#each tasks as task }
    <div class='col-span-1 w-fit-content h-20 bg-yellow rounded shadow-lg'>    
        <Task task={task}/>
    </div>
    {/each}
</div>