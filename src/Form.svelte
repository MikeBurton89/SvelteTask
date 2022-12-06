<script lang="ts">
  import TaskContainer from "./TaskContainer.svelte";
  type TaskType ={
    value: string,
    date: string
    user: string
  }
  
    let taskValue : TaskType 
    let tasksArray : TaskType[]= []
    console.table(tasksArray)

    const inputHandler =(event: Event)=> {
      event.preventDefault()
          taskValue = {
            value: (event.currentTarget as HTMLInputElement).value,
            date: new Date(Date.now()).toLocaleDateString(),
            user: 'UserName'}
    }

    const saveHandler =(event: MouseEvent)=> {
      event.preventDefault()
      try{
        if(taskValue.value !== ''){
        tasksArray =[...tasksArray, taskValue]
      }
      }catch(error){
        console.log(error)
      }
      
    }

    const clearHandler=(event: MouseEvent)=> {
      event.preventDefault()
      tasksArray = []
    }
    // let tasks =localStorage.setItem('tasks', JSON.stringify(tasksArray))
</script>

<form class="w-screen max-w-lg px-6 py-6 mt-5 bg-yellow rounded shadow-lg">
  <div class="flex flex-wrap -mx-3 mb-6">
    <div class="w-full px-3">
      <label class="block uppercase tracking-wide text-dark-blue text-xs font-bold mb-2" for="grid-password">
        Task
      </label>
      <input on:input={inputHandler} class="appearance-none block w-full text-black border border-pewter rounded py-3 px-4 mb-3 leading-tight focus:outline-none focus:bg-white focus:border-blue-gray" id="grid-password" type="text">
      <p class="text-dark-blue text-xs italic">Insert a Task</p>
      <button on:click={saveHandler} class="bg-dark-blue hover:bg-blue-gray hover:text-dark-blue text-pewter mt-2 font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline" type="button">
        Save
      </button>
      <button disabled={tasksArray.length === 0 ? true : false} on:click={clearHandler} class="bg-dark-blue hover:bg-blue-gray hover:text-dark-blue text-pewter disabled:bg-pewter disabled:text-yellow mt-2 font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline" type="button">
        Clear
      </button>
    </div>
  </div>
</form>
{#if tasksArray.length !== 0}
    <TaskContainer tasks={tasksArray}/>
{/if}