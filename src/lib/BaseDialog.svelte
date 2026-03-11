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
		if (show) {
			dialog?.showModal();
		} else if (dialog?.open) {
			// Capture the precise scroll position before the browser acts
			const scrollY = window.scrollY;
			const scrollX = window.scrollX;

			dialog?.close();

			// Defer the scroll restoration until the browser has finished its native focus jump
			setTimeout(() => {
				window.scrollTo({ left: scrollX, top: scrollY, behavior: 'instant' });
			}, 0);
		}
	});
</script>

<dialog
	class="border-none relative max-w-[90vw] max-h-[90vh] w-auto h-auto overflow-hidden rounded-xl p-0 bg-transparent shadow-2xl"
	id="main"
	bind:this={dialog}
	onclose={() => { show = false; }}
	onclick={(e) => {
		if (e.target === dialog) show = false;
	}}
>
	<div class="absolute -top-50 -right-50 h-96 w-96 rounded-full bg-[#5e2338] blur-[100px] z-10"></div>
	<X class="absolute right-0 top-0 text-[#f3f781] m-4 hover:cursor-pointer hover:scale-150 transition duration-300 ease-out z-10" size="32" onclick={()=>{show=false}}/>
	{@render children?.()}
</dialog>

<style>
    #main {
        margin: auto;
        border-radius: 0.75rem;
        border: none;

        &::backdrop {
            background-color: rgba(0, 0, 0, 0.4);
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