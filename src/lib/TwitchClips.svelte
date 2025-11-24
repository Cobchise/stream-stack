<script lang="ts">
	import { onMount } from 'svelte';
	import { env } from '$env/dynamic/public';

	interface ClipData {
		id: string;
		thumbnail_url: string;
		title: string;
		url: string;
		view_count: number;
		duration: number;
	}

	let loading = true;
	let token_data = null;
	let access_token: string | null = null;
	export let data: ClipData[] | null = null;

	onMount(async () => {
		try {
			const token_response = await fetch('https://id.twitch.tv/oauth2/token', {
				method: 'POST',
				headers: {
					'Content-Type': 'application/json'
				},
				body: JSON.stringify({
					client_id: env.PUBLIC_TWITCH_CLIENT_ID,
					client_secret: env.PUBLIC_TWITCH_CLIENT_SECRET,
					grant_type: 'client_credentials'
				})
			});
			if (token_response.ok) {
				const token_data = await token_response.json();
				access_token = token_data['access_token'];
			}

			const response = await fetch(
				`https://api.twitch.tv/helix/clips?broadcaster_id=${env.PUBLIC_BROADCASTER_ID}&is_featured=True`,
				{
					headers: {
						'Client-ID': env.PUBLIC_TWITCH_CLIENT_ID,
						Authorization: `Bearer ${access_token}`
					}
				}
			);
			if (response.ok) {
				const res = await response.json();
				data = res.data;
				loading = false;
				console.log(data);
			}
		} catch (err: unknown) {
			if (err instanceof Error) {
				console.log(err.message);
			}
		}
	});
</script>

{#if !loading}
<div class="grid grid-cols-3 gap-4">
	{#each data as clip}
		<div class="card bg-base-100 w-96 shadow-sm">
			<figure>
				<img src={clip['thumbnail_url']} alt="Twitch clip" />
			</figure>
			<div class="card-body">
				<h2 class="card-title">{clip['title']}</h2>
			</div>
		</div>
	{/each}
</div>
{/if}
