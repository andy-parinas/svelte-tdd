<script>
    import {scale, fade} from 'svelte/transition'
    let selectedIndex = 0;

    const changeSecondTab = (index) => {
        selectedIndex = index;
    }

    const animate = (node, args) =>
		args.cond ? fade(node, args) : scale(node, args);
</script>

<!-- svelte-ignore a11y-click-events-have-key-events -->
<div class="vertical-tab-container">
    <ul class="vertical-tab">
        <li class:selected={selectedIndex == 0} class="button"
            on:click={() => changeSecondTab(0)}>First Tab</li>
        
        <li class:selected={selectedIndex == 1} class="button"
            on:click={() => changeSecondTab(1)}>Second Tab</li>

        <li class:selected={selectedIndex == 2} class="button"
            on:click={() => changeSecondTab(2)}>Third Tab</li>
    </ul>

    <div class="vertical-tab-content">
        {#if selectedIndex == 0}
            <div transition:animate={(selectedIndex == 0)}>
                <h2>First Tab Heading</h2>
                <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Autem aut deserunt veniam tempora deleniti quos reprehenderit natus. Animi, obcaecati dolorum, culpa, maiores maxime ullam soluta unde rerum nihil temporibus quibusdam!</p>
            </div>
        {:else if selectedIndex == 1}
            <div transition:animate={(selectedIndex == 1)}>
                <h2>Second Tab Heading</h2>
                <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Autem aut deserunt veniam tempora deleniti quos reprehenderit natus. Animi, obcaecati dolorum, culpa, maiores maxime ullam soluta unde rerum nihil temporibus quibusdam!</p>
            </div>
        {:else if selectedIndex == 2}
        <div transition:animate={(selectedIndex == 2)}></div>
            <h2>Third Tab Heading</h2>
            <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Autem aut deserunt veniam tempora deleniti quos reprehenderit natus. Animi, obcaecati dolorum, culpa, maiores maxime ullam soluta unde rerum nihil temporibus quibusdam!</p>
        
        {/if}


    </div>
</div>

<style>
    .button {
        cursor: pointer;
    }
    .vertical-tab-container {
        display: flex;
        flex-direction: row;
        align-items: center;
        border: 1px solid gray;
        border-radius: 1rem;
    }

    .vertical-tab {
        margin: 0px;
        padding: 3rem;
        list-style: none;
        border-right: 1px solid gray
    }

    .vertical-tab li {
        margin: 2rem 0;
    }

    .vertical-tab-content {
        flex:1
    }
    .selected {
        color: blue;
    }
</style>