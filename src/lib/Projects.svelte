<script lang="ts">
	import { onMount } from 'svelte';
	import { SquareCheck, Square } from 'lucide-svelte';

	interface StageData {
		id: number;
		checked: boolean;
		description: string;
	}

	interface ProjectData {
		id: number;
		thumbnail_url: string;
		title: string;
		description: string;
		progress: number;
		stages: StageData[];
	}

	let loading = true;
	export let projects: ProjectData[] | null = null;

	onMount(async () => {
		try {
			projects = [
				{
					id: 1,
					thumbnail_url:
						'https://media.istockphoto.com/id/1147544807/vector/thumbnail-image-vector-graphic.jpg?s=612x612&w=0&k=20&c=rnCKVbdxqkjlcs3xH87-9gocETqpspHFXu5dIGB4wuM=',
					title: 'Test project',
					description: 'This is a test project',
					progress: 50,
					stages: [
						{
							id: 1,
							checked: true,
							description: 'Repo created'
						},
						{
							id: 2,
							checked: true,
							description: 'Code uploaded'
						},
						{
							id: 3,
							checked: true,
							description: 'App deployed'
						}
					]
				},
				{
					id: 2,
					thumbnail_url:
						'https://media.istockphoto.com/id/1147544807/vector/thumbnail-image-vector-graphic.jpg?s=612x612&w=0&k=20&c=rnCKVbdxqkjlcs3xH87-9gocETqpspHFXu5dIGB4wuM=',
					title: 'Test project 2',
					description: 'This is a second test project',
					progress: 75,
					stages: []
				},
				{
					id: 3,
					thumbnail_url:
						'https://media.istockphoto.com/id/1147544807/vector/thumbnail-image-vector-graphic.jpg?s=612x612&w=0&k=20&c=rnCKVbdxqkjlcs3xH87-9gocETqpspHFXu5dIGB4wuM=',
					title: 'Test project 3',
					description: 'This is a third test project',
					progress: 100,
					stages: []
				}
			];
			loading = false;
		} catch (err: unknown) {
			if (err instanceof Error) {
				console.log(err.message);
			}
		}
	});
</script>

{#if !loading}
	<h1 class="p-7 text-left text-4xl">Projects</h1>

	<div class="bg-base-200 pt-14 pr-7 pb-14 pl-7">
		<div class="card lg:card-side bg-base-300shadow-sm max-h-80">
			<figure>
				<img src={projects[0].thumbnail_url} alt={projects[0].title} class="rounded-4xl" />
			</figure>

			<div class="card-body">
				<h2 class="card-title">{projects[0].title}</h2>
				<p>{projects[0].description}</p>
				<progress class="progress progress-info w-56" value={projects[0].progress} max="100"
				></progress>
				<div class="card-actions justify-end">
					<button class="btn btn-primary">View</button>
				</div>
			</div>

			{#if projects[0].stages.length > 0}
				<ul class="timeline timeline-vertical">
                    <li>
                        <div class="timeline-middle">
                            {#if projects[0].stages[0].checked == true}
                                <SquareCheck class="stroke-purple-600" />
                            {:else}
                                <Square />
                            {/if}
                        </div>
                        <div class="timeline-start timeline-box">{projects[0].stages[0].description}</div>
                        <hr class="bg-purple-800" />
                    </li>
					{#each projects[0].stages.slice(1,-1) as stage}
						<li>
							<hr class="bg-purple-800" />
							<div class="timeline-middle">
								{#if stage.checked == true}
									<SquareCheck class="stroke-purple-600" />
								{:else}
									<Square />
								{/if}
							</div>
							<div class="timeline-start timeline-box">{stage.description}</div>
							<hr class="bg-purple-800" />
						</li>
					{/each}
                    <li>
                        <hr class="bg-purple-800" />
                        <div class="timeline-middle">
                            {#if projects[0].stages.slice(-1)[0].checked == true}
                                <SquareCheck class="stroke-purple-600" />
                            {:else}
                                <Square />
                            {/if}
                        </div>
                        <div class="timeline-start timeline-box">{projects[0].stages.slice(-1)[0].description}</div>
                    </li>
				</ul>
			{/if}
		</div>
	</div>

	<div class="grid grid-cols-2 gap-20 p-14">
		{#each projects as project}
			<div class="card card-border lg:card-side bg-base-300 max-h-50 border-purple-900 shadow-sm">
				<figure class="p-7">
					<img src={project.thumbnail_url} alt={project.title} class="mask mask-hexagon-2" />
				</figure>
				<div class="card-body">
					<h2 class="card-title">{project.title}</h2>
					<p>{project.description}</p>
					<progress class="progress progress-info w-56" value={project.progress} max="100"
					></progress>
					<div class="card-actions justify-end">
						<button class="btn btn-primary">View</button>
					</div>
				</div>
			</div>
		{/each}
	</div>
{/if}
