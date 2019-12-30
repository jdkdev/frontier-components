<script>
    export let type = 'text'
    export let value
    export let name
    export let label = name.replace('_', ' ')
    export let placeholder = name
    export let errors = []
    export let help = ''
</script>

<fieldset class="field">
    <label for={name}>{label}</label>
    <div class='control'>
        {#if type === 'text'}
            <input type='text' {name} bind:value={value} {placeholder}>
        {:else if type === 'password'}
            <input type='password' {name} bind:value={value} {placeholder}>
        {:else if type === 'hidden'}
            <input type='hidden' {name} bind:value={value} {placeholder}>
        {:else}
            <input type='text' {name} bind:value={value} {placeholder}>
        {/if}
    </div>
    {#if errors.length}
        <p class='error'>{errors[0]}</p>
    {:else if help}
        <p class='help'>{help}</p>
    {/if}
</fieldset>

<style>
    label {
        text-transform: capitalize;
    }
</style>
