<script lang="ts">
    import Counter from '../lib/components/counter.svelte';
    import Dice from '../lib/components/dice.svelte';
    import Button from '../lib/components/button.svelte';
    
    const roll = () => {
        const roll = Math.floor(Math.random() * 6) + 1;

        return roll;
    }

    let lock = false;
    
    const soldiers = { attack: 0, defense: 0 }
    
    const dices: { attack: number[], defense: number[] } = {
        attack: [],
        defense: []
    }
    
    const rollMany = (type: 'attack' | 'defense') => {
        console.log(dices[type].length)
        for (let i = 0; i < dices[type].length; i++) {
            dices[type][i] = roll();
        }
    }

    const sort = (type: 'attack' | 'defense') => {
        dices[type] = dices[type].sort((a, b) => b - a);
    }

    const check = () => {
        for (let i = 0; i < 3; i++) {
            if (dices.attack[i] > dices.defense[i]) {
                if (soldiers.defense === 0) return
                soldiers.defense -= 1;
            } else {
                if (soldiers.attack === 0) return
                soldiers.attack -= 1;
            }
        }
    }

    const battle = () => {
        if (soldiers.attack === 0) return
        if (soldiers.defense === 0) return

        rollMany('attack');
        rollMany('defense');

        sort('attack');
        sort('defense');

        check()
    }

    const reset = () => {
        soldiers.attack = 0;
        soldiers.defense = 0;
    }

    const start = () => {
        lock = true;
    }

    const stop = () => {
        lock = false;
    }

    $: {
        dices.attack = dices.attack.slice(0, soldiers.attack);

        for (let i = 0; i < Math.min(soldiers.attack, 3); i++) {
            dices.attack[i] ??= roll();
            sort('attack');
        }
    }

    $: {
        dices.defense = dices.defense.slice(0, soldiers.defense);

        for (let i = 0; i < Math.min(soldiers.defense, 3); i++) {
            dices.defense[i] ??= roll();
            sort('defense');
        }
    }

</script>

<div class="p-8 w-screen h-screen flex flex-col justify-between items-center">
    <Counter bind:count={soldiers.attack}  />

    <div class="flex gap-2">
        {#each dices.attack as number}
            <Dice type="attack" number={number} />
        {/each}
    </div>

    <div class="flex flex-col gap-2">
        {#if !lock}
            <Button on:click={start} disabled={!soldiers.attack || !soldiers.defense}>
                Start
            </Button>
        {:else}
            <Button on:click={battle}>
                Battle
            </Button>
        {/if}
        {#if !lock && (soldiers.attack && soldiers.defense)}
            <Button on:click={stop}>
                Stop
            </Button>
        {:else}
            <Button on:click={reset}>
                Reset
            </Button>
        {/if}
    </div>

    <div class="flex gap-2">
        {#each dices.defense as number}
            <Dice type="defense" number={number} />
        {/each}
    </div>

    <Counter bind:count={soldiers.defense} />
</div>


