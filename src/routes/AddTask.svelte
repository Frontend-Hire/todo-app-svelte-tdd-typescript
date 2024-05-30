<script lang="ts">
  export let addTask: (taskName: string) => void;

  let taskName = '';

  const onAddTask = () => {
    if (!taskName.trim()) return;

    addTask(taskName);

    taskName = '';
  };
</script>

<form on:submit|preventDefault={onAddTask}>
  <label for="task-input">Add Task: </label>
  <input id="task-input" bind:value={taskName} required />
  <button>Add</button>
</form>
