<script lang='ts'>
	let likes:number = 123581321
	let src:string = 'https://i.pinimg.com/originals/c9/9c/98/c99c98936a66370a09589509ca274001.gif';
	let icon:string = 'far fa-heart'
	function like(){
		likes++
		icon='fas fa-heart has-text-danger'
	}

</script>

<div class='is-flex is-flex-direction-column is-align-items-center'>
	<div>
		<figure class='image'>
			<img {src} alt="Dancing Yisus">
		</figure>
		<div class='column is-flex is-justify-content-space-between p-0 has-background-light has-text-left'>
			<button class='is-2 button has-background-light'
				on:click|once={like}>
				<i class={icon}/>
			</button>
			<p class="column is-10 is-size-4 pb-0 pt-0 has-text-centered">{likes}</p>
		</div>
	</div>
</div>