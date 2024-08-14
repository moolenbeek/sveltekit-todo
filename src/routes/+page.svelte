<script>
	import { focusTrap } from '@skeletonlabs/skeleton';
	export let data;
</script>

<div class="container m-auto max-w-xs">
	<h1>todos</h1>

	<form use:focusTrap={true} method="POST" action="?/create">
		<label>
			add a todo:
			<input data-focusindex="0" name="description" autocomplete="off" class="input" type="text" placeholder="Input" />
		</label>
	</form>

	<ul class="list my-4">
		{#each data.todos as todo (todo.id)}
			<li>
				<form method="POST" action="?/delete">
					<div class="input-group input-group-divider grid-cols-[auto_1fr_auto]">
						<input type="hidden" name="id" value={todo.id} />
						<span class="mx-4">{todo.description}</span>
						<button class="variant-soft-error" aria-label="Mark as complete">-</button>
					</div>
				</form>
			</li>
		{/each}
	</ul>
</div>
