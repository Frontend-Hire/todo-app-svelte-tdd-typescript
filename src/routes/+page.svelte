<script lang="ts">
  type Priority = 'p1' | 'p2' | 'p3';

  type Task = {
    id: number;
    title: string;
    isCompleted: boolean;
    priority?: Priority;
  };

  let tasks: Task[] = [];

  let taskName = '';

  const addTask = () => {
    const trimmedTaskName = taskName.trim();

    if (!trimmedTaskName) return;

    tasks = [
      ...tasks,
      { id: new Date().getTime(), title: trimmedTaskName, isCompleted: false },
    ];
    taskName = '';
  };

  const onKeydown = (e: KeyboardEvent) => {
    if (e.key === 'Enter') addTask();
  };
</script>

<div>
  <h1>Tasks</h1>
  <label for="task-input">Add Task: </label>
  <input id="task-input" bind:value={taskName} on:keydown={onKeydown} />
  <button on:click={addTask}>Add</button>
  <ul>
    {#each tasks as task (task.id)}
      <li>{task.title}</li>
    {/each}
  </ul>
</div>
