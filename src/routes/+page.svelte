<script lang="ts">
  import { afterUpdate } from 'svelte';
  import type { Task } from '../types';
  import AddTask from './AddTask.svelte';

  let tasks: Task[] = [];

  const addTask = (taskName: string) => {
    tasks = [
      ...tasks,
      { id: new Date().getTime(), title: taskName, isCompleted: false },
    ];
  };

  afterUpdate(() => {
    console.log('Page Rendered');
  });
</script>

<div>
  <h1>Tasks</h1>
  <AddTask {addTask} />
  <ul>
    {#each tasks as task (task.id)}
      <li>{task.title}</li>
    {/each}
  </ul>
</div>
