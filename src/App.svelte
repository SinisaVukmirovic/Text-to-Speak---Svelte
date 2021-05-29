<script>
    import { } from 'os';
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
    let text = '';
    let selectedVoice;

    onMount(() => {
        speechSynthesis.onvoiceschanged = () => {
            // console.log(speechSynthesis.getVoices(), 'voices');
            voices = speechSynthesis.getVoices();
            selectedVoice = voices[0];
        }
    });

    const printVoice = voice => {
        if (!voice) {
            return '';
        } 
        return `${voice.name} (${voice.lang})`;
    }

    const play = () => {
        
    }
</script>

<style>
    :global(body) {
        width: 90%;
        max-width: 30rem;
        margin: 5rem auto;
    }
</style>

<!-- markup (zero or more items) goes here -->
<Container>
    <Row>
        <Col>
            <h2>Speak To Me</h2>
        </Col>
    </Row>

    <Row>
        <Col>
            <FormGroup>
                <Label for="words">Say something..</Label>
                <Input type="text" id="words" bind:value={text} />
            </FormGroup>
        </Col>
    </Row>

    <Row>
        <Col>
            <FormGroup>
                <Label for="voices">Say something..</Label>
                <Input type="select" id="voices" bind:value={selectedVoice}>
                    {#each voices as voice}
                        <option value={voice}>{printVoice(voice)}</option>
                    {/each}
                </Input>
            </FormGroup>
        </Col>
    </Row>

    <Row>
        <Col>
            <FormGroup>
                <Label for="pitch">Pitch</Label>
                <Input type="range" id="pitch" bind:value={pitch}
                min="0.1" max="2" step="0.1">
                </Input>
            </FormGroup>
        </Col>
    </Row>

    <Row>
        <Col>
            <FormGroup>
                <Label for="rate">Rate</Label>
                <Input type="range" id="rate" bind:value={rate}
                min="0.1" max="2" step="0.1">
                </Input>
            </FormGroup>
        </Col>
    </Row>

    <Row>
        <Col>
            <FormGroup>
                <Label for="volume">Volume</Label>
                <Input type="range" id="rate" bind:value={volume}
                min="0.1" max="1" step="0.1">
                </Input>
            </FormGroup>
        </Col>
    </Row>

    <Row>
        <Col>
            <FormGroup>
                <Button on:click={play} color="primary">Play</Button>
            </FormGroup>
        </Col>
    </Row>

    <Row>
        <Col>
        
        </Col>
    </Row>
</Container>