<script>
	export let count = 0;

    const add = () => {
        count += 1;
    }

    const subtract = () => {
        count -= 1;
    }

    const addTen = () => {
        count += 10;
    }

    const subtractTen = () => {
        count -= 10;
    }

</script>

<div class="counter">
    <button disabled={count < 10} on:click={subtractTen}>-10</button>
    <button disabled={count < 1} on:click={subtract}>-</button>
    <span>{count}</span>
    <button disabled={count > 1000} on:click={add}>+</button>
    <button disabled={count > 1000 - 10} on:click={addTen}>+10</button>
</div>

<style lang="scss">

    .counter {
        display: flex;
        justify-content: center;
        align-items: center;
        gap: 1rem;

        button {
            padding: .5rem 1rem;
            border: none;
            background-color: #f1f1f1;
            cursor: pointer;
        }

        span {
            font-size: 2rem;
        }
    }
  
</style>