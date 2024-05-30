<script lang="ts">
  import type { Task } from '../types';
  import AddTask from './AddTask.svelte';
  import TaskList from './TaskList.svelte';
  import TaskListHeader from './TaskListHeader.svelte';
  import TaskListItem from './TaskListItem.svelte';

  let tasks: Task[] = [];

  const addTask = (taskName: string) => {
    tasks = [
      ...tasks,
      { id: new Date().getTime(), title: taskName, isCompleted: false },
    ];
  };
</script>

<div>
  <h1>Tasks</h1>
  <AddTask {addTask} />
  <TaskList>
    <TaskListHeader slot="header" count={tasks.length} />
    {#each tasks as task (task.id)}
      <TaskListItem>{task.title}</TaskListItem>
    {/each}
  </TaskList>
</div>
