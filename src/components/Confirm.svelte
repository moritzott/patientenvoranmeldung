<script>
    import { createEventDispatcher } from "svelte";
    const dispatch = createEventDispatcher();

    export let personData;

    const cancelSubmit = () => {
        dispatch("cancel-submit");
    };


    const submitData = () => {
        console.log(`Transfering data to a backend API: `);
        console.log(personData);
        dispatch("data-has-been-sent");
    };

    
</script>
<div >
    <p class="p-5 pb-1 ">
        Sie haben folgenden Patienten mit diesen Daten eingegeben:
    </p>
    <p class="p-5">
        <span class="has-text-weight-bold">Name:</span> {personData.firstname} {personData.lastname} <br>
        <span class="has-text-weight-bold">Alter:</span> {personData.age}<br> <span class="has-text-weight-bold">Geschlecht:</span> {personData.sex} <br>
        
    </p>
    <p class="p-5">
        <span class="has-text-weight-bold">War davor bei einem Arzt:</span> {personData.sentFromADoctor}
    </p>

    <p class="p-5">
        <span class="has-text-weight-bold">Symptome:</span> <br>
        {personData.symptoms}
        <br>
    </p>

    <p class="has-background-warning p-5">
        Wollen Sie die Daten senden und den Patienten ankündigen?
    </p>
    <div class="level is-mobile mt-5">
        <button on:click="{cancelSubmit}" class="button m-1 mb-5 level-item is-danger">&larr; Abbrechen</button>
        <button on:click="{submitData}" class="button m-1 mb-5 level-item is-primary">Anmelden &rarr;</button>
    </div>

    
</div>