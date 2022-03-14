<script lang='ts'>
	import DancingYisus from "./components/DancingYisus.svelte";
	let name:string = 'visitor';
	let showYisus:boolean = false;
	$: console.log(showYisus);
	function yisus(){
		if (showYisus) alert("Once he starts dancing you can't stop watching him")
		showYisus = true
		}
</script>

<style>
	.bg-img{
		background-image: url('https://c4.wallpaperflare.com/wallpaper/460/269/170/the-simpsons-homer-simpson-wallpaper-preview.jpg');
		background-size: cover;
		background-repeat: no-repeat;
	}
</style>

<div class='hero is-fullheight'>
	<section class="hero is-primary is-small pb-0">
		<div class="hero hero-header has-text-centered">
				<p class="title m-0">
					Compu-Global-Hyper-Mega-Net
				</p>
		<div class="hero hero-body p-0">			
				<p class="is-size-7	">
					<a href='https://leomonay.github.io/' target='_blank' rel="noopener noreferrer">Leo Monay's</a> Svelte, Bulma.io & TypeScript first project
				</p>
		</div>
		<div class="hero hero-body p-3">			
			<p class="subtitle p-0">
				Welcome, {name.toUpperCase()}!
			</p>
		</div>
	</section>
	<div class="column bg-img m-0 is-flex is-justify-content-right">
		<div class='column has-text-centered is-8'>
			<div>	
				<button class='button is-primary m-1'
				on:click="{yisus}">
					{#if showYisus==false}
						Just show me dancing Yisus!
					{:else}
						Hide Yisus please!
					{/if}
					</button>
			</div>
			{#if showYisus==true}
				<DancingYisus/>
			{/if}
		</div>
	</div>
</div>