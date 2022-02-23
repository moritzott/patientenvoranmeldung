<script>
    import { createEventDispatcher } from "svelte";
    import { onMount } from "svelte";
    

    const dispatch = createEventDispatcher();


    let numberOne = 0;
    let numberTwo = 1;
    $: sum = parseInt(numberOne) + parseInt(numberTwo);
    let userGuessedSum;

    const setRandomNumbers = () => {
        numberOne = Math.floor(Math.random() * 10) + 1;
        numberTwo = Math.floor(Math.random() * 10) + 1;
    };

    // beim Laden in das DOM: Zufallszahlen setzen!
    onMount(() => {
        setRandomNumbers();
    });

    const checkCaptcha = () => {
        if (parseInt(userGuessedSum) === sum){
            return true;
        }
        return false;
    };

    let message = {
        firstname: "",
        lastname: "",
        sex: "Mann",
        age: 0,
        symptoms: "",
        sentFromADoctor: "Nein",
    };

    // function to confirm Data
    const getData = () => {
        // console.log("Ich war hier");
        dispatch("get-form-data", message);
    };

    // function to cancel the form
    function cancelForm() {
        dispatch("cancel-form");
    };

    function checkAndSubmit() {
        if (checkCaptcha()) {
            getData();
        }
    };
</script>


<form class="m-4 pb-4" on:submit|preventDefault="{checkAndSubmit}" action="#">
    <div class="field has-text-centered">
        <h3 class="is-size-5-mobile is-size-4-desktop is-size-4-tablet">Infos zum Patienten</h3>
    </div>
    <div class="field">
        <label for="firstname" class="label">Vorname</label>
        <input type="text" class="input" bind:value="{message.firstname}" name="firstname" id="" required>
    </div>
    <div class="field">
        <label for="lastname" class="label">Nachname</label>
        <input type="text" class="input" bind:value="{message.lastname}" name="lastname" id="" required>
    </div>
    <div class="field">
        <label for="sex" class="label">Geschlecht</label>
        <div class="control">
            <div class="select">
                <select name="sex"  bind:value="{message.sex}">
                    <option value="Mann" >Mann</option>
                    <option value="Frau">Frau</option>
                </select>
            </div>
        </div>
    </div>
    <div class="field">
        <label for="age" class="label">Alter</label>
        <input bind:value="{message.age}" type="number" min="0" max="110" class="input" name="age" required id="">
    </div>
    <div class="field">
        <label for="description" class="label">Symptome/Grund für Besuch</label>
        <textarea bind:value="{message.symptoms}" name="description"  cols="30" rows="10" class="textarea"></textarea>
    </div>
    <div class="field">
        <label class="label" for="sent">Waren Sie davor bei einem Arzt?</label>
        <div class="control">
            <label for="sent" class="radio">
                <input type="radio" name="sent" value="Ja" bind:group="{message.sentFromADoctor}" >
                Ja
            </label>
            <label for="sent" class="radio">
                <input type="radio" name="sent" value="Nein" bind:group="{message.sentFromADoctor}" >
                Nein
            </label>
        </div>
    </div>

    <!-- Foto hochladen -->
    <!-- <div class="field">
        <label for="photo" class="label">Foto von Wunde etc. (optional)</label>
        <div class="file">
            <div class="file-label is-info">
                <input class="file-input" type="file" name="foto" id="">
                <span class="file-cta">
                    
                </span>
                Datei auswählen...
            </div>
        </div>   
    </div> -->
    <br>
    <!-- Captcha Abfrage -->
    <div class="field">
        <label class="has-text-weight-bold" for="abfrage">Sicherheitsfrage:</label>
        <p >Bitte berechnen Sie folgende Summe: </p> 
        <br>
        <div class="">
            <div class=" inline ">
                <span class="mt-5">{numberOne} + {numberTwo} = </span>
            </div>
            <div class="inline ">
                <input id="userGuess" class="input" type="number" name="userGuess" bind:value="{userGuessedSum}" required>
            </div>
        </div>
        
        
    </div>
    <br>
    <div class="level is-mobile mt-5">
      
        <button on:click|preventDefault="{cancelForm}" class="button is-danger level-item">&larr; Abbrechen</button>
        <input type="submit" value="Weiter &rarr;" class="button is-primary level-item">
        <!-- <button class=" button is-primary">Weiter &rarr;</button> -->
  
    </div>

</form>

<style>
    #userGuess {
        width: 80px;
        font-size: 0.8rem;
        height: 2.5em;


    }

    .inline {
        display: inline;
    }
</style>