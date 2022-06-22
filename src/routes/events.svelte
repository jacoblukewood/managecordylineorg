<script>
	import FieldSet from "$lib/FieldSet.svelte";
	import LabeledInput from "$lib/LabeledInput.svelte";
</script>

<FieldSet>
	<LabeledInput label="Name" />
	<LabeledInput label="Date & Time" type="datetime-local" />
	<LabeledInput label="Location" type="autocomplete-full-address" />
	<LabeledInput label="Event Name" type="textarea" />
	<LabeledInput label="Event Name" />
</FieldSet>
