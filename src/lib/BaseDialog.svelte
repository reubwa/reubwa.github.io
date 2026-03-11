<script lang="ts">
	import type { Snippet } from "svelte";
	import { X } from '@lucide/svelte';
	let {
		show = $bindable(),
		dialog = $bindable(),
		children
	}: {
		show: boolean,
		dialog? : HTMLDialogElement,
		children : Snippet
	} = $props();
	$effect(() => {
		if (show) dialog?.showModal();
		else dialog?.close();
	});
</script>

<dialog
	class="border-none relative min-h-screen h-screen overflow-x-hidden"
	id="main"
	bind:this={dialog}
	onclose={() => (show = false)}
	onclick={(e) => {
		if (e.target === dialog) dialog.close();
	}}
>
	<div class="absolute -top-50 -right-50 h-96 w-96 rounded-full bg-[#5e2338] blur-[100px]"></div>
	<X class="absolute right-0 text-[#f3f781] mr-2.5 mt-2.5 hover:cursor-pointer hover:scale-150 transition duration-300 ease-out" size="32" onclick={()=>{show=false}}/>
	{@render children?.()}
</dialog>

<style>
    #main {
        margin: auto;
        border-radius: 0.2em;
        border: none;

        &::backdrop {
            background-color: rgba(0, 0, 0, 0.3);
        }
        &[open] {

            animation: zoom 0.3s cubic-bezier(0.34, 1.56, 0.64, 1);
            &::backdrop {
                animation: fade 0.2s ease-out;
            }
        }
    }

    @keyframes zoom {
        from {
            transform: scale(0.98);
        }
        to {
            transform: scale(1);
        }
    }

    @keyframes fade {
        from {
            opacity: 0;
        }
        to {
            opacity: 1;
        }
    }
</style>