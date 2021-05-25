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

    onMount(() => {
        speechSynthesis.onvoiceschanged = () => {
            console.log(speechSynthesis.getVoices(), 'voices');
        }
    });
</script>

<style>
    /* your styles go here */
</style>

<!-- markup (zero or more items) goes here -->