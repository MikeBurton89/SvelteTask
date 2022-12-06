<script lang='ts'>
    import Task from "./Task.svelte";
    export let tasks: TaskType[]
    type TaskType ={
    value: string
    date: string
    user: string
  }
</script>

<div class='grid-cols-1 grid lg:grid-cols-4 gap-2.5 mt-5 px-6 py-6 w-screen h-fit-content bg-blue-gray justify-items-center'>
    {#each tasks as task }
    <div class='col-span-1 w-fit-content bg-yellow rounded shadow-lg h-fit'>    
        <Task task={task}/>
    </div>
    {/each}
</div>