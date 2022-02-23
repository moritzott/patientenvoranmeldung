<script>
	import Card from "./components/Card.svelte";
	import Heading from "./components/Heading.svelte";
	import Welcome from "./components/Welcome.svelte";
	import Form from "./components/Form.svelte";
	import Footer from "./components/Footer.svelte";
	import Confirm from "./components/Confirm.svelte";
	import SuccessModal from "./components/SuccessModal.svelte";

	let cardContent = Welcome;
	let props;


	function getPersonDataFromForm (event) {
		let data = event.detail;
		// console.log(data);
		props = {personData :data};
		cardContent = Confirm;

	};

	
</script>

<main>
	<div class="m-5">
		<Heading />
		
		<Card>
			{#if (cardContent == Welcome || cardContent == Form || cardContent == SuccessModal)}
				<svelte:component this={cardContent} on:show-home={() => {cardContent = Welcome}} on:get-form-data={getPersonDataFromForm} on:cancel-form={() => { cardContent = Welcome}} on:show-form={() => { cardContent = Form }} />
			{:else if (cardContent == Confirm )}
				<svelte:component this={cardContent} on:data-has-been-sent={() => { cardContent = SuccessModal; }} on:cancel-submit={() => {cardContent = Welcome}} {...props} />
			{/if}		
			
		</Card>

	</div>


	<Footer />

	
</main>

<style>
	main {
		max-width: 450px;
		margin-left: auto;
		margin-right: auto;
	}
</style>