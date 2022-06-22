<script type="ts">
	import { nanoid } from "nanoid";

	export let label = "";
	export let placeholder = "";
	export let type = "text";
	export let autocomplete = "off";
	export let value = "";
	export let description = "";

	const id = nanoid();

	const baseInputClasses = "bg-black bg-opacity-5 p-2";
</script>

<svelte:head>
	<script
		async
		src="https://maps.googleapis.com/maps/api/js?key=AIzaSyAhyPeYyo2XqM6eZ1Jk7ULAitVXEAJ50vs&libraries=places&callback=initMap">
		const input = document.getElementById(id) as HTMLInputElement;
		const options = {
			bounds: defaultBounds,
			componentRestrictions: { country: "us" },
			fields: ["address_components", "geometry", "icon", "name"],
			strictBounds: false,
			types: ["establishment"]
		};

		const autocomplete = new google.maps.places.Autocomplete(input, options);
	</script>
</svelte:head>

<div class="flex flex-col space-y-1">
	<label for={id}>{label}</label>
	{#if type === "autocomplete-full-address"}
		<input {id} type="text" {placeholder} {value} class={baseInputClasses} />
	{:else if type === "textarea"}
		<textarea class={baseInputClasses} />
	{:else}
		<input {id} {type} {autocomplete} {placeholder} {value} class={baseInputClasses} />
	{/if}
	<p>{description}</p>
</div>
