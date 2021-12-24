<script>
    import { TextArea, CopyButton, TextInput } from "carbon-components-svelte";

    let value = "";
    $: output = value.match(/\d{18}/g) || [];
</script>

<main>
    <h2>Extract Discord IDs From Texts</h2>
    <TextArea labelText="Input" placeholder="Enter Text" bind:value />
    <TextInput
        labelText="Only parse lines with text"
        placeholder="Enter text..."
    />
    <TextArea
        labelText="Ouput"
        disabled
        helperText={output.length && `${output.length} IDs found`}
        value={output.join(" ")}
    />

    {#if output.length}
        <div class="wrapper">
            <CopyButton text={output.join(" ")} />
        </div>
    {/if}
</main>

<style>
    main {
        text-align: center;
        padding: 1em;
        max-width: 800px;
        margin: 0 auto;
    }

    .wrapper {
        display: flex;
        justify-content: center;
        margin: 10px;
    }

    h2 {
        color: #5865f2;
        text-transform: uppercase;
    }
</style>
