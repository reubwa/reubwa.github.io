<script lang="ts">
	import './layout.css';
	import favicon from '$lib/assets/favicon.svg';

	let { children } = $props();
</script>

<svelte:head>
	<link rel="icon" href={favicon} />
	<!-- HTML Meta Tags -->
	<title>Reuben Waring&#039;s Website</title>
	<meta name="description" content="Sheffield-based Computer Science student looking for a placement/internship opportunity" />

	<!-- Google / Search Engine Tags -->
	<meta itemprop="name" content="Reuben Waring&#039;s Website" />
	<meta itemprop="description" content="Sheffield-based Computer Science student looking for a placement/internship opportunity" />
	<meta itemprop="image" content="https://reubwa.github.io/IMG_2946.JPG" />

	<!-- Facebook Meta Tags -->
	<meta property="og:url" content="https://reubwa.github.io/" />
	<meta property="og:type" content="website" />
	<meta property="og:title" content="Reuben Waring&#039;s Website" />
	<meta property="og:description" content="Sheffield-based Computer Science student looking for a placement/internship opportunity" />
	<meta property="og:image" content="https://reubwa.github.io/IMG_2946.JPG" />

	<!-- Twitter Meta Tags -->
	<meta name="twitter:card" content="summary_large_image" />
	<meta name="twitter:title" content="Reuben Waring&#039;s Website" />
	<meta name="twitter:description" content="Sheffield-based Computer Science student looking for a placement/internship opportunity" />
	<meta name="twitter:image" content="https://reubwa.github.io/IMG_2946.JPG" />

	<!-- Meta Tags Generated via https://heymeta.com -->
</svelte:head>
{@render children()}
