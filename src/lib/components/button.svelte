<script>
    export let disabled = false;
</script>

<button class="button" on:click disabled={disabled}>
    <slot />
</button>

<style lang="scss">

    .button {
        padding: .5rem 1rem;
        border: none;
        background-color: #f1f1f1;
        cursor: pointer;
    }

    .button:hover {
        background-color: #e1e1e1;
    }

    .button:active {
        background-color: #d1d1d1;
    }

    .button:disabled {
        background-color: #f1f1f1;
        cursor: not-allowed;
    }

    .button:focus {
        outline: none;
    }

    .button:active:focus {
        outline: none;
    }

    .button:disabled:focus {
        outline: none;
    }

    .button:active:disabled {
        background-color: #f1f1f1;
    }

    .button:active:disabled:focus {
        outline: none;
    }

    .button:active:disabled:hover {
        background-color: #f1f1f1;
    }
    
</style>