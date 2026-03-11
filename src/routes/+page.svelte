<script lang="ts">
	import Button from '$lib/Button.svelte';
	import { ListTree, ZoomIn } from '@lucide/svelte';
	import BaseDialog from '$lib/BaseDialog.svelte';
	let scrollY = 0;
	const scrollThreshold = 600;
	let showPresentLightbox = false;
	let showJSONistLightbox = false;
</script>

<svelte:window bind:scrollY />

<svelte:head>
	<title>Reuben Waring's Website</title>
</svelte:head>

<div class="flex flex-col justify-center items-center min-h-screen w-full">
	<div class="flex flex-col-reverse md:flex-row justify-center items-center gap-8 md:gap-12 max-w-6xl w-full px-6 md:px-12 pt-6 md:pt-12">
		<div class="flex flex-col w-full md:w-1/2 text-center md:text-left" id="top">
			<h1 class="ibm-plex-serif-bold mb-4">Hi!
				<br> I'm Reuben Waring</h1>
			<p class="ibm-plex-mono-regular mb-4">I'm a second year Computer Science student at Sheffield Hallam University and keen programmer.
				On here, you'll find a varied selection of my projects from both University and personal work.</p>
			<a href="#projects" class="ibm-plex-mono-regular text-lg underline">↓ Projects</a>
		</div>
		<div class="flex flex-col w-full md:w-1/2 text-center md:text-left gap-3.5 items-center">
			<img src="/IMG_2946.JPG" alt="Reuben Waring Headshot" class="rounded-full w-48 h-48 md:w-80 md:h-80 object-cover"/>
			<div class="flex flex-row w-full md:w-1/2 text-center md:text-left gap-2.5 items-center justify-center">
				<Button label="Github" href="github.com/reubwa" icon="Github"/>
				<Button label="LinkedIn" href="linkedin.com/in/reubenwaring" icon="Linkedin"/>
			</div>
		</div>
	</div>

	<div class="flex flex-row sticky top-0 w-full justify-center bg-[#5e2338] z-10 py-4 mt-8 transition-discrete duration-300 {scrollY > scrollThreshold ? 'border-b-[#f3f781] border-b' : 'border-0'}">
		<div class="flex flex-row gap-2.5 md:gap-4 mr-3 md:mr-0 items-center pl-6 transition-opacity duration-300 {scrollY > scrollThreshold ?
'opacity-100' : 'opacity-0 pointer-events-none'}">
			<h4 class="ibm-plex-serif-bold">Reuben Waring</h4>
			<Button label="" href="github.com/reubwa" icon="Github"/>
			<Button label="" href="linkedin.com/in/reubenwaring" icon="Linkedin"/>
			<button class="ibm-plex-mono-regular flex flex-row gap-2.5 bg-[#f3f781] text-[#5e2338] rounded-[20px] w-fit p-2.5 text-center" title="Contents">
				<ListTree/>
				Contents
			</button>
		</div>
	</div>

	<div class="flex flex-col max-w-6xl w-full gap-4 px-6 md:px-12 pb-6 md:pb-12 mt-8" id="projects">
		<div class="flex flex-row items-center gap-4">
			<h2 class="ibm-plex-serif-bold">Projects</h2>
			<a href="#top" class="ibm-plex-mono-regular text-lg underline">↑ Top</a>
		</div>
		<div class="flex flex-col-reverse md:flex-row rounded-xl border-[#f3f781] border overflow-clip gap-2">
			<div class="relative cursor-pointer" on:click={()=>{showPresentLightbox=true}}>
				<img src="/present2.jpeg" alt="Screenshot of Present 2" class=" h-fit md:h-30 w-full md:w-63">
				<ZoomIn class="absolute bottom-0 right-0 mb-2.5 mr-2.5"/>
			</div>
			<div class="flex flex-col p-2.5 md:p-0 -mt-5 md:m-0">
				<h4 class="ibm-plex-sans-600">Present 2</h4>
				<p class="s ibm-plex-sans-400">Web-based Reveal.js presentation editor with support for transitions, markdown and PDF export.
					Written in Svelte.</p>
			</div>
			<div class="overflow-x-hidden flex flex-row md:flex-col mt-2 mr-2 mb-2 md:min-w-34 md:max-w-34 ml-2 gap-2 p-2.5 md:p-0">
				<Button label="Source" href="github.com/reubwa/present2" icon="Github" grow={true} cl="w-full"/>
				<Button label="Try" href="reubwa.github.io/present2/" icon="Play" grow={true} cl="w-full"/>
			</div>
		</div>
		<div class="flex flex-col-reverse md:flex-row rounded-xl border-[#f3f781] border overflow-clip gap-2">
			<div class="relative cursor-pointer" on:click={()=>{showJSONistLightbox=true}}>
				<img src="/jsonist.png" alt="Screenshot of JSONist" class=" h-fit md:h-30 w-full md:w-69">
				<ZoomIn class="absolute bottom-0 right-0 mb-2.5 mr-2.5"/>
			</div>
			<div class="flex flex-col p-2.5 md:p-0 -mt-5 md:m-0">
				<h4 class="ibm-plex-sans-600">JSONist</h4>
				<p class="s ibm-plex-sans-400">Desktop tool for analysing Network Rail Tiplocs, including performing LINQ queries and filtering.
					Written in C# and WinForms.</p>
			</div>
			<div class="overflow-x-hidden flex flex-row md:flex-col mt-2 mr-2 mb-2 md:min-w-fit md:max-w-fit ml-2 gap-2 p-2.5 md:p-0">
				<Button label="Source" href="github.com/reubwa/jsonist" icon="Github" grow={true} cl="w-full"/>
				<Button label="Download" href="github.com/reubwa/JSONist/releases/latest" icon="Download" grow={true} cl="w-full"/>
			</div>
		</div>
	</div>
</div>
<BaseDialog bind:show={showPresentLightbox}>
	<img src="/present2.jpeg" alt="Screenshot of Present 2" class="object-cover w-full h-full max-w-full max-h-full min-w-full min-h-full"/>
</BaseDialog>
<BaseDialog bind:show={showJSONistLightbox}>
	<img src="/jsonist.png" alt="Screenshot of JSONist" class="w-full h-full max-w-full max-h-full min-w-full min-h-full"/>
</BaseDialog>
<style>

    a:hover {
        text-decoration: none;
    }

    button{
        border: 1px solid transparent;
    }

    button:hover {
        cursor: pointer;
        background-color: #5e2338;
        border-color: #f3f781;
        color: #f3f781;
    }
</style>