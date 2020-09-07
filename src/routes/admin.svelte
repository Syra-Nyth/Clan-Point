<style>
    table {
        margin-left: auto;
        margin-right: auto;
    }

    td {
        text-align: center !important;
    }

    input {
        width: 80px;
    }

    button {
        margin-top: 30px;
        margin-left: auto;
        margin-right: auto;
        padding-left: 20px;
        padding-right: 20px;
    }

</style>

<script>
    import { stores } from '@sapper/app'
    const { session } = stores()

    let holdScores = session.clans

    // session.clans = {
    holdScores = {
        balmoral: [1, 1, 1, 1, 1, 1],
        braemar: [1, 1, 1, 1, 1, 1],
        doune: [1, 1, 1, 1, 1, 1],
        dunvegan: [1, 1, 1, 1, 1, 1],
        glamis: [1, 1, 1, 1, 1, 1],
        stirling: [1, 1, 1, 1, 1, 1],
    }

    function addScore() {
       session.clans = holdScores
       console.log("No")
     }
</script>

<br>
<br>
<br>
<!-- Table -->
<div>
    <table class="table is-bordered table is-striped">
        <tbody>
            <!-- Table Head -->
            <tr>
                <td>Clan</td>
                <td>Athletics</td>
                <td>Swimming Sports</td>
                <td>Rangi Roadie</td>
                <td>Clan Quiz</td>
                <td>Cross Country</td>
                <td>Clan Singing</td>
                <td>Total</td>
            </tr>
            <!-- Balmoral -->
            <tr>
                <td>Balmoral</td>
                {#each holdScores.balmoral as score}
                    <td>
                        <input type="number" bind:value={score}>
                    </td>
                {/each}
            </tr>
            <!-- Braemar -->
            <tr>
                <td>Braemar</td>
                {#each holdScores.braemar as score}
                    <td>
                        <input type="number" bind:value={score}>
                    </td>
                {/each}
            </tr>
            <!-- Doune -->
            <tr>
                <td>Doune</td>
                {#each holdScores.doune as score}
                    <td>
                        <input type="number" bind:value={score}>
                    </td>
                {/each}
            </tr>
            <!-- Dunvegan -->
            <tr>
                <td>Dunvegan</td>
                {#each holdScores.dunvegan as score}
                    <td>
                        <input type="number" bind:value={score}>
                    </td>
                {/each}
            </tr>
            <!-- Glamis -->
            <tr>
                <td>Glamis</td>
                {#each holdScores.glamis as score}
                    <td>
                        <input type="number" bind:value={score}>
                    </td>
                {/each}
            </tr>
            <!-- Sterling -->
            <tr>
                <td>Stirling</td>
                {#each holdScores.stirling as score}
                    <td>
                        <input type="number" bind:value={score}>
                    </td>
                {/each}
            </tr>
        </tbody>
    </table>
</div>

<!-- Buttons -->
<div class="field is-grouped">
    <button class="button is-success is-light" on:click={addScore}>Save</button>
    <button class="button is-danger is-light" type="reset">Reset</button>
</div>