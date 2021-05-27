<script>
    import { onMount } from 'svelte';

    import {
        Col,
        Container,
        Row,
        Input,
        Label,
        FormGroup,
        Button,
    } from "sveltestrap";

    let voices = [];
    let rate = 1;
    let pitch = 1;
    let volume = 1;

    onMount(() => {
        speechSynthesis.onvoiceschanged = () => {
            // console.log(speechSynthesis.getVoices(), 'voices');
            voices = speechSynthesis.getVoices();
        }
    });
</script>

<style>
    /* your styles go here */
</style>

<!-- markup (zero or more items) goes here -->