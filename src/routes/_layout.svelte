<script>
	import Header from './_components/Header.svelte'
	import Nav from './_components/Nav.svelte'
	import Footer from './_components/Footer.svelte'

	export let segment
</script>

<style>
</style>

<Header />

<Nav {segment}/>

<main class="section">
	<slot></slot>
</main>

<Footer />