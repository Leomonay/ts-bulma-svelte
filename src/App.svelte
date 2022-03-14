<script lang='ts'>
	import DancingYisus from "./components/DancingYisus.svelte";
	let name:string = 'visitor';
	let clickCounter:number = 0;
	let showYisus:boolean = false;
	$: console.log(showYisus);
	function yisus(){
		if (showYisus) alert("Once he starts dancing you cant stop watching him")
		showYisus = true
		}
	let src:string = 'https://i.pinimg.com/originals/c9/9c/98/c99c98936a66370a09589509ca274001.gif';
	export {DancingYisus}
</script>

<style>
	.bg-img{
		background-image: url('https://c4.wallpaperflare.com/wallpaper/460/269/170/the-simpsons-homer-simpson-wallpaper-preview.jpg');
		background-size: cover;
		background-repeat: no-repeat;
	}
</style>

<div class='hero is-fullheight'>
	<section class="hero hero-head is-primary">
		<div class="hero hero-body">
				<p class="title">
					Compu-Global-Hyper-Mega-Net
				</p>
		<div class="hero hero-footer">			
				<p class="subtitle">
					Welcome, {name.toUpperCase()}!
				</p>
		</div>
	</section>
	<div class="column bg-img m-0 is-flex is-justify-content-right">
		<div class='column has-text-centered is-6'>
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
				<div class="column is-8 is-offset-2 ">
					<figure class='image is-2by3'>
						<img {src} alt="Shesus dances.">
					</figure>
				</div>
			{/if}
		</div>
	</div>
</div>