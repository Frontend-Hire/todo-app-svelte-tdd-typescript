<script lang="ts">
  type Priority = 'p1' | 'p2' | 'p3';

  type Task = {
    id: number;
    title: string;
    isCompleted: boolean;
    priority?: Priority;
  };

  const tasks: Task[] = [
    {
      id: 1,
      title: 'Learn Svelte',
      isCompleted: true,
      priority: 'p1',
    },
  ];
</script>

<div>
  <h1>Tasks</h1>
  <ul>
    {#each tasks as task (task.id)}
      <li>{task.title}</li>
    {/each}
  </ul>
</div>
