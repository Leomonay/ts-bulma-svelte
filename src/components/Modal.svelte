<script lang='ts'>
  export let show:boolean, close:Function, action:Function;
  let negClicks:number = 0;
  let messages:string[] = [
    "Let him dance",
    "Look at him! He's happy doing it",
    "Like him, at least, please",
    "Cm'on, let him dance",
    "Be a friend...",
    "Ok, if it is your real will..."
  ];
  let src:string='/assets/asFriends.png';
  
  function handleCancel(){
    src = (negClicks === messages.length-2) ?'/assets/okay.png' : '/assets/asFriends.png'
    if (negClicks < messages.length-1){
      negClicks++
    }else if (negClicks = messages.length-1){
      action()
      negClicks=0
    }
    close()
  }
  interface Target{
    removeEventListener: Function
  }
  interface Event {
    keyCode : number;
    target: Target
  }
  function escape(event:Event){
    if (event.keyCode === 27) { // Escape key
      event.target.removeEventListener('keydown', escape);
      close();
    }
  }
  document.addEventListener('keydown', escape)
  window.addEventListener('keydown', escape)
</script>

<style></style>

<div class="modal" style={`display: ${show?'block':'none'}`}>
  <div class="modal-background"></div>
  <div class="modal-card m-auto">
    <header class="modal-card-head is-justify-content-space-between">
      <div>
        <p class="modal-card-title mr-2">Once he starts, you can't stop watching him</p>
      </div>
      <button class="delete" aria-label="close" on:click={close()}></button>
    </header>
    <section class="modal-card-body is-flex is-justify-content-space-between is-align-items-center p-0 has-background-dark">
      <div class="column is-10">
        <p class='is-size-4 has-text-light'>
          <i>"{messages[negClicks]}"</i>
        </p>
      </div>
      <div class="column is-2 pb-0 pr-0">
        <figure class='image'>
          <img src={src} alt='detective begging to Bob Sideshow'/>
        </figure>  
      </div>
    </section>
    <footer class="modal-card-foot is-flex is-justify-content-center">
      {#if negClicks !== messages.length-1}
        <button class="button is-success" on:click={close()}>Let him dance</button>
      {/if}
      <button class={`button ${negClicks === messages.length-1? 'is-danger' : ''}`} on:click={handleCancel}>Please, hide him</button>
    </footer>
  </div>
</div>