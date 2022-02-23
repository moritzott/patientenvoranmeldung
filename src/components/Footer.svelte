<script>


    let text = "INFO";
    let infoModal;

    function toggleInfo() {
        infoModal.classList.toggle("is-active");
    };

</script>

<div id="infoLink" class="has-text-centered">
    <span on:click="{toggleInfo}" class=" is-link is-underlined">{text}</span>
</div>

<!-- Info Modal to show when clicked -->
<div bind:this="{infoModal}" class="modal">
    <div on:click="{toggleInfo}" class="modal-background"></div>
    <div class="modal-content">
        <div class="box m-4 p-5">
            <h4 class="has-text-weight-semibold is-size-4-mobile is-size-3-desktop is-size-3-tablet has-text-centered">Beschreibung</h4>
            <p class="m-3">Die Patientenvoranmeldung ist eine (noch im Testmodus befindliche) Anwendung
                zur elektronischen Voranmeldung von Patienten, die die Notfallambulanz oder die Notfallpraxis
                eines Krankenhauses aufsuchen möchten. Durch Angabe von Informationen zum Patienten und zu den
                Symptomen (inkl. evtl. Fotos) kann die Aufnahme schneller erfolgen und das Personal die eingehenden Fälle
                noch vor dem Eintreffen im Krankenhaus besser einordnen oder gar Patienten vorab an andere passendere Adressen verweisen.
            </p>
            <h4 class="has-text-weight-semibold is-size-4-mobile is-size-3-desktop is-size-3-tablet has-text-centered">Kontakt</h4>
            <p class="m-3">Wenn Sie Fragen haben oder Erweiterungen vorschlagen möchten: <br>
            </p>
            <div class="has-text-centered">
                <img src="img/contactMail.png" alt="Mailcontact" width="250px;">
            </div>
            
            
            <h4 class="has-text-weight-semibold is-size-4-mobile is-size-3-desktop is-size-3-tablet has-text-centered">Komponenten</h4>
            <p class="m-3">Für die Icons wurde die Schriftart <em>Roboto</em> verwendet, deswegen muss ich hier eine entsprechende Information kundtun:</p>
            <p class="ml-3">Komponente: Roboto</p>
            <p class="ml-3">Lizenzgeber: Google Inc.</p>
            <p class="ml-3">Lizenz: <a href="https://www.apache.org/licenses/LICENSE-2.0.html" target="_blank">Apache License v2.0</a></p>
            <h4 class="has-text-weight-semibold is-size-4-mobile is-size-3-desktop is-size-3-tablet has-text-centered">Version</h4>
            <p class="m-3">Aktuelle Version ist 1.0.0</p>
        </div>
    </div>
    <button on:click="{toggleInfo}" class="modal-close is-large"></button>
</div>


<style>
    span {
        cursor: pointer;
    }

    img {
        margin-left: auto;
        margin-right: auto;
    }



</style>