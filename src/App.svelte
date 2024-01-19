<script>
    import Navbar from "./section/Navbar.svelte";
    import Form from "./UI/Form.svelte";
    import VCard from "./section/VCard.svelte";

    let QRCode="";
    let values;
</script>

<style>
    main {
        padding : 1rem;
        max-width: 600px;
        margin: 0 auto;
    }
</style>

<Navbar title="vCard Generator" />


<main>
    <Form
    bind:values
    on:createQRCode={e=>{
        QRCode=e.detail;
    }} />
    <VCard {values} {QRCode} />
</main>