<script>
	import { onMount } from 'svelte'
	import axios from 'axios'

	let visits = []
	let backendConnected = false
	let nameInput

	const getVisits = () => {
		axios.get('http://localhost:5000/visits')
			.then((response) => {
				visits = response.data.visits
				backendConnected = true
			}).catch((error) => {
				backendConnected = false
				console.log(error)
			})
	}
	const addVisit = () => {
		axios.post('http://localhost:5000/visits', {
			name: nameInput
		}).then((response) => {
			nameInput = ''
			getVisits()
			}).catch((error) => {
				console.log(error)
			})
	}

	const handleKeyPressOrder = (event) => {
		if (event.keyCode === 13) {
			addVisit()
		}
	}

	onMount(() => {
		getVisits()
	})
	
</script>

<main>
	<div id="wrapper">
		<h1>Visitor history</h1>
		{#if backendConnected}
			<input 
				type="text" 
				placeholder="Enter username."
				bind:value={nameInput}
				on:keypress={handleKeyPressOrder}
				/>
				<br>
			<table>
				<tr>
					<th>visitor</th>
					<th>visit date</th>
				</tr>
				{#each visits as visit, idx}
					<tr>
						<td>{visit.visitor_name}</td>
						<td>{visit.visit_datetime}</td>
					</tr>
				{/each}
			</table>
		{:else}
			<div>Couldn't connect to the backend</div>
		{/if}
	</div>
</main>

<style>
	#wrapper {
		margin: 64px auto;
		width: 560px;
		text-align: center;
	}
	h1 {
		font-weight: bold;
		font-size: 2em;
		margin-bottom: 24px;
	}
	input {
		padding: 8px 12px;
		font-size: 1rem;
		width: 320px;
		text-align: center;
	}
	table {
		width: 100%;
		margin-top: 36px;
		text-align: center
	}
	table tr > * {
		height: 40px;
		line-height: 40px;
	}
	table th {
		border-bottom: 2px solid #ddd;
	}
	table td {
		border-bottom: 1px solid #eee;
	}
</style>