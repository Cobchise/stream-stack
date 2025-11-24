<script lang="ts">
	import { onMount } from 'svelte';
	import { env } from '$env/dynamic/public';
	import { Eye, Timer } from 'lucide-svelte';

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
	<div class="grid grid-cols-3 gap-4 p-7">
		{#each data as clip}
			<div class="hover-3d">
				<!-- content -->
				<figure class="relative rounded-2xl">
					<img src={clip['thumbnail_url']} alt="Twitch Clip" />
					<div class="absolute top-0 left-0 w-full">
						<div class="absolute top-2 left-2">
							<h3 class="card-title">{clip['title']}</h3>
						</div>
						<div class="absolute top-40 left-5 text-center shadow-2xl">
							<Eye />
							{clip['view_count']}
						</div>
						<div class="absolute top-40 right-5 text-center shadow-2xl">
							<Timer />
							{clip['duration']}
						</div>
					</div>
				</figure>

				<!-- 8 empty divs needed for the 3D effect -->
				<div></div>
				<div></div>
				<div></div>
				<div></div>
				<div></div>
				<div></div>
				<div></div>
				<div></div>
			</div>
		{/each}
	</div>
{/if}
