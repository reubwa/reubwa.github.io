<script lang="ts">
	let { icon, label, href, cl = "", grow = false } = $props();
	import { Github, Linkedin, Play, Download, SquareArrowOutUpRight } from '@lucide/svelte';
</script>
<a class="no-underline text-inherit {cl}" href="https://{href}" title={label} target="_blank">
	<div class="ibm-plex-mono-regular flex flex-row gap-2.5 bg-[#f3f781] text-[#5e2338] rounded-[20px] {grow ? 'w-full' : 'w-fit'} p-2.5 text-center">
		{#if icon === "Github"}
			<Github/>
		{:else if icon === "Linkedin"}
			<Linkedin/>
		{:else if icon === "Play"}
			<Play/>
		{:else if icon === "Download"}
			<Download/>
		{:else if icon === "Read"}
			<SquareArrowOutUpRight />
		{/if}
		{label}
	</div>
</a>
<style>
    div {
        border: 1px solid transparent;
    }

    div:hover {
        cursor: pointer;
        background-color: #5e2338;
        border-color: #f3f781;
        color: #f3f781;
    }
</style>