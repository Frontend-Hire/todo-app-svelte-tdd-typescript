<script lang="ts">
  type Priority = 'p1' | 'p2' | 'p3';

  type Task = {
    id: number;
    title: string;
    isCompleted: boolean;
    priority?: Priority;
  };

  let tasks: Task[] = [
    {
      id: 1,
      title: 'Learn Svelte',
      isCompleted: true,
      priority: 'p1',
    },
  ];

  let taskName = '';

  const addTask = () => {
    tasks = [
      ...tasks,
      { id: new Date().getTime(), title: taskName, isCompleted: false },
    ];
  };
</script>

<div>
  <h1>Tasks</h1>
  <label for="task-input">Add Task: </label>
  <input id="task-input" bind:value={taskName} />
  <button on:click={addTask}>Add</button>
  <ul>
    {#each tasks as task (task.id)}
      <li>{task.title}</li>
    {/each}
  </ul>
</div>
