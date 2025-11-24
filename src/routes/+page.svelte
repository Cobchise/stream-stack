<script lang="ts">
	import Logo from '$lib/assets/cob.png';
</script>

<!-- NavBar Start -->

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

<!-- NavBar End -->

<!-- Hero Start -->

<div class="hero bg-base-200 min-h-screen">
	<div class="hero-content flex-col lg:flex-row-reverse">
		<img src={Logo} alt="Cobchise Logo" class="w-32 rounded-lg shadow-2xl" />
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

<!-- Clip Carousel Start -->

<div class="carousel carousel-center rounded-box">
	<div class="carousel-item">
		<img
			src="https://img.daisyui.com/images/stock/photo-1559703248-dcaaec9fab78.webp"
			alt="Pizza"
		/>
	</div>
	<div class="carousel-item">
		<img
			src="https://img.daisyui.com/images/stock/photo-1565098772267-60af42b81ef2.webp"
			alt="Pizza"
		/>
	</div>
	<div class="carousel-item">
		<img
			src="https://img.daisyui.com/images/stock/photo-1572635148818-ef6fd45eb394.webp"
			alt="Pizza"
		/>
	</div>
	<div class="carousel-item">
		<img
			src="https://img.daisyui.com/images/stock/photo-1494253109108-2e30c049369b.webp"
			alt="Pizza"
		/>
	</div>
	<div class="carousel-item">
		<img
			src="https://img.daisyui.com/images/stock/photo-1550258987-190a2d41a8ba.webp"
			alt="Pizza"
		/>
	</div>
	<div class="carousel-item">
		<img
			src="https://img.daisyui.com/images/stock/photo-1559181567-c3190ca9959b.webp"
			alt="Pizza"
		/>
	</div>
	<div class="carousel-item">
		<img
			src="https://img.daisyui.com/images/stock/photo-1601004890684-d8cbf643f5f2.webp"
			alt="Pizza"
		/>
	</div>
</div>

<!-- Clip Carousel End -->

<!-- Footer Start -->

<footer class="footer sm:footer-horizontal bg-neutral text-neutral-content items-center p-4">
	<aside class="grid-flow-col items-center">
		<svg
			width="36"
			height="36"
			viewBox="0 0 24 24"
			xmlns="http://www.w3.org/2000/svg"
			fill-rule="evenodd"
			clip-rule="evenodd"
			class="fill-current"
		>
			<path
				d="M22.672 15.226l-2.432.811.841 2.515c.33 1.019-.209 2.127-1.23 2.456-1.15.325-2.148-.321-2.463-1.226l-.84-2.518-5.013 1.677.84 2.517c.391 1.203-.434 2.542-1.831 2.542-.88 0-1.601-.564-1.86-1.314l-.842-2.516-2.431.809c-1.135.328-2.145-.317-2.463-1.229-.329-1.018.211-2.127 1.231-2.456l2.432-.809-1.621-4.823-2.432.808c-1.355.384-2.558-.59-2.558-1.839 0-.817.509-1.582 1.327-1.846l2.433-.809-.842-2.515c-.33-1.02.211-2.129 1.232-2.458 1.02-.329 2.13.209 2.461 1.229l.842 2.515 5.011-1.677-.839-2.517c-.403-1.238.484-2.553 1.843-2.553.819 0 1.585.509 1.85 1.326l.841 2.517 2.431-.81c1.02-.33 2.131.211 2.461 1.229.332 1.018-.21 2.126-1.23 2.456l-2.433.809 1.622 4.823 2.433-.809c1.242-.401 2.557.484 2.557 1.838 0 .819-.51 1.583-1.328 1.847m-8.992-6.428l-5.01 1.675 1.619 4.828 5.011-1.674-1.62-4.829z"
			></path>
		</svg>
		<p>Copyright © {new Date().getFullYear()} - All right reserved</p>
	</aside>
	<nav class="grid-flow-col gap-4 md:place-self-center md:justify-self-end">
		<a>
			<svg
				xmlns="http://www.w3.org/2000/svg"
				width="24"
				height="24"
				viewBox="0 0 24 24"
				class="fill-current"
			>
				<path
					d="M19.615 3.184c-3.604-.246-11.631-.245-15.23 0-3.897.266-4.356 2.62-4.385 8.816.029 6.185.484 8.549 4.385 8.816 3.6.245 11.626.246 15.23 0 3.897-.266 4.356-2.62 4.385-8.816-.029-6.185-.484-8.549-4.385-8.816zm-10.615 12.816v-8l8 3.993-8 4.007z"
				></path>
			</svg>
		</a>
	</nav>
</footer>

<!-- Footer End -->
