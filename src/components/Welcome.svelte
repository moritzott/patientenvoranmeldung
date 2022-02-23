<script>
    import { createEventDispatcher } from "svelte";




    const dispatch = createEventDispatcher();

    function startForm () {
        dispatch("show-form");
    };

</script>
<div >
    <p class="p-5 pb-1">
        Melden Sie sich oder einen Patienten vorab an. <br>
        Dann können wir besser planen.
    </p>
    <div class="has-text-right">
        <button on:click="{startForm}" class=" mr-3 mb-4  button is-primary is-medium">
            Los geht's!
        </button>
    </div>
    
</div>


<style>
    button {
        
        font-weight: bold;
    }
</style>