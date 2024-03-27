<script>
	import { isPreviewing, Content} from '@builder.io/sdk-svelte';

	// Create an array of your custom components and their properties
	const CUSTOM_COMPONENTS = [
		
	];

	// this data comes from the function in `+page.server.js`, which runs on the server only
	export let data;

	// we want to show unpublished content when in preview mode.
	const canShowContent = data.content || isPreviewing();
</script>

<svelte:head>
	<title>Home</title>
</svelte:head>

<main>
	{#if canShowContent}
		<Content
			model="page"
			content={data.content}
			apiKey={import.meta.env.VITE_BUILDER_PUBLIC_API_KEY}
			customComponents={CUSTOM_COMPONENTS}
		/>
	{:else}
		Content Not Found
	{/if}
</main>