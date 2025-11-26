<script lang="ts">
	import Logo from '$lib/assets/cob.png';
    import TwitchClips from '$lib/TwitchClips.svelte'
	import Projects from '$lib/Projects.svelte'
    import { SiTwitch, SiYoutube } from '@icons-pack/svelte-simple-icons'
</script>

<!-- NavBar Start -->

<!--
<div class="navbar bg-base-100 shadow-sm">
	<div class="flex-1">
		<a class="btn btn-ghost text-xl">cobchise</a>
	</div>

	<div class="flex-none">
		<button class="btn btn-square btn-ghost">
			<svg
				xmlns="http://www.w3.org/2000/svg"
				fill="none"
				viewBox="0 0 24 24"
				class="inline-block h-5 w-5 stroke-current"
			>
				<path
					stroke-linecap="round"
					stroke-linejoin="round"
					stroke-width="2"
					d="M5 12h.01M12 12h.01M19 12h.01M6 12a1 1 0 11-2 0 1 1 0 012 0zm7 0a1 1 0 11-2 0 1 1 0 012 0zm7 0a1 1 0 11-2 0 1 1 0 012 0z"
				></path>
			</svg>
		</button>
	</div>
</div>
-->

<!-- NavBar End -->

<!-- Hero Start -->

<div class="hero bg-base-200 min-h-screen">
	<div class="hero-content flex-col lg:flex-row-reverse">
		<img src={Logo} alt="Cobchise Logo" class="w-32 rounded-lg" />
		<div class="max-w-md">
			<h1 class="text-5xl font-bold">Hello there</h1>
			<p class="py-6">Welcome to my personal site/blog</p>
			<span class="text-rotate text-2xl">
				<span class="justify-items-center">
					<span>HACKING</span>
					<span>PHOTOGRAPHY</span>
					<span>GAMING</span>
					<span>3D PRINTING</span>
				</span>
			</span>
		</div>
	</div>
</div>

<!-- Hero End -->

<div class="grid grid-cols-1">

<!-- Clips Start -->

<TwitchClips />

<!-- Clips End -->

<!-- Projects Start -->

<Projects />

<!-- Projects End -->

</div>

<!-- Footer Start -->

<footer class="footer sm:footer-horizontal bg-neutral text-neutral-content items-center p-4">
	<aside class="grid-flow-col items-center">
		<p>Copyright © {new Date().getFullYear()} - All right reserved</p>
	</aside>
	<nav class="grid-flow-col gap-4 md:place-self-center md:justify-self-end">
		<a href="https://www.twitch.tv/cobchise" target="_blank">
            <SiTwitch />
		</a>
        <a href="https://www.youtube.com/@cobchise7464" target="_blank">
            <SiYoutube />
        </a>
	</nav>
</footer>

<!-- Footer End -->
