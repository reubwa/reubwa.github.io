<script lang="ts">
	let { icon, label, href } = $props();
	import { Github, Linkedin } from '@lucide/svelte';
</script>
<a class="no-underline text-inherit" href="https://{href}" title={label} target="_blank">
	<div class="ibm-plex-mono-regular flex flex-row gap-2.5 bg-[#f3f781] text-[#5e2338] rounded-[20px] w-fit p-2.5 text-center">
		{#if icon === "Github"}
			<Github/>
		{:else if icon === "Linkedin"}
			<Linkedin/>
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