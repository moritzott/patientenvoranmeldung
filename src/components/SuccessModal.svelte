<script>
    import {createEventDispatcher} from "svelte";
    const dispatch = createEventDispatcher();


</script>

<div >
    <div class="p-5 field has-text-centered">
        <h3 class="is-size-5-mobile is-size-4-desktop is-size-4-tablet">Vielen Dank!</h3>
    </div>
    <p class="p-5 pb-1 ">
        Die Informationen wurden erfolgreich übermittelt.
    </p>
    <p class="p-5">
        
    <div class="has-text-centered mt-5">
        
        <button on:click="{() => { dispatch("show-home") }}" class="button m-3 mb-5 is-primary">OK</button>
    </div>

    
</div>