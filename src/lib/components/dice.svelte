<script>
	export let type = 'attack'
    export let number = 6;
</script>

<div class="dice face-{number} {type}">
    {#each {length: number} as _}
        <span class="dot" />
    {/each}
</div>

<style lang="scss">

    .dice {
        width: 1.5em;  
        height: 1.5em;  
        border-radius: .25em;
        position: relative;

        &.attack { background-color: #da121a; }

        &.defense { background-color: #fcdd09; }
        
        .dot {
            width: .3em;
            height: .3em;
            background-color:white;
            border-radius: 50%;
            position: absolute;
            transform: translate(-50%, -50%);
        }
    }


    .face-1 {
        .dot:nth-of-type(1) { top: 50%; left: 50%; }
    }

    .face-2 {
        .dot:nth-of-type(1) { top: 20%; left: 20%; }
        .dot:nth-of-type(2) { top: 80%; left: 80%; }
    }

    .face-3 {
        .dot:nth-of-type(1) { top: 20%; left: 20%; }
        .dot:nth-of-type(2) { top: 50%; left: 50%; }
        .dot:nth-of-type(3) { top: 80%; left: 80%; }
    }

    .face-4 {
        .dot:nth-of-type(1) { top: 20%; left: 20%; }
        .dot:nth-of-type(2) { top: 20%; left: 80%; }
        .dot:nth-of-type(3) { top: 80%; left: 20%; }
        .dot:nth-of-type(4) { top: 80%; left: 80%; }
    }

    .face-5 {
        .dot:nth-of-type(1) { top: 20%; left: 20%; }
        .dot:nth-of-type(2) { top: 20%; left: 80%; }
        .dot:nth-of-type(3) { top: 50%; left: 50%; }
        .dot:nth-of-type(4) { top: 80%; left: 20%; }
        .dot:nth-of-type(5) { top: 80%; left: 80%; }
    }

    .face-6 {
        .dot:nth-of-type(1) { top: 20%; left: 20%; }
        .dot:nth-of-type(2) { top: 50%; left: 20%; }
        .dot:nth-of-type(3) { top: 80%; left: 20%; }
        .dot:nth-of-type(4) { top: 20%; left: 80%; }
        .dot:nth-of-type(5) { top: 50%; left: 80%; }
        .dot:nth-of-type(6) { top: 80%; left: 80%; }
        .dot:nth-of-type(6) { top: 80%; left: 80%; }
    }
  
</style>