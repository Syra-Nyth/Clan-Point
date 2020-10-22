<script>
  import Nav from "./_components/Nav.svelte";

  import { stores } from "@sapper/app";
  const { session } = stores();

  // Provides a filler number for the table, until it is fetched from the database
  let holdScores = {
    balmoral: [1, 1, 1, 1, 1, 1, 1],
    braemar: [1, 1, 1, 1, 1, 1, 1],
    doune: [1, 1, 1, 1, 1, 1, 1],
    dunvegan: [1, 1, 1, 1, 1, 1, 1],
    glamis: [1, 1, 1, 1, 1, 1, 1],
    stirling: [1, 1, 1, 1, 1, 1, 1]
  };

  // saves the clan placings to the database, overriding anything already there
  function saveClan() {
    console.log("saveClan() clicked");
    // save the clan placings to the database under the clan name
    console.log(session.clans);
    db.collection("clans")
      .doc("placings")
      .set(session.clans);
  }

  // fetches the clan placings from the database
  async function getClan() {
    // get the document from the database for the given clan
    let clanDoc = await db
      .collection("clans")
      .doc("placings")
      .get();

    // get the data from the clan document
    holdScores = clanDoc.data();
  }

  getClan();

  /*If the session.clans data is not found (is 'falsey'), then this data will be used a placeholder for the table until the correct data can be inserted.*/
  if (!session.clans) {
    session.clans = {
      balmoral: [0, 0, 0, 0, 0, 0, 0],
      braemar: [0, 0, 0, 0, 0, 0, 0],
      doune: [0, 0, 0, 0, 0, 0, 0],
      dunvegan: [0, 0, 0, 0, 0, 0, 0],
      glamis: [0, 0, 0, 0, 0, 0, 0],
      stirling: [0, 0, 0, 0, 0, 0, 0]
    };
  }
</script>

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
    margin-left: auto;
    margin-right: auto;
    padding-left: 20px;
    padding-right: 20px;
  }

  div {
    margin-top: 50px;
    margin-bottom: 50px;
  }
</style>

<div>
  <Nav />
  <!-- Table -->
  <div>
    <table class="table is-bordered table is-striped">
      <tbody>
        <!-- Table Head -->
        <tr>
          <td>Clan</td>
          <td>400m</td>
          <td>Athletics</td>
          <td>Swimming Sports</td>
          <td>Rangi Roadie</td>
          <td>Clan Quiz</td>
          <td>Clan Singing</td>
          <td>Total</td>
        </tr>
        <!-- Balmoral -->
        <tr>
          <td>Balmoral</td>
          {#each session.clans.balmoral as score}
            <td>
              <input type="number" bind:value={score} />
            </td>
          {/each}
        </tr>
        <!-- Braemar -->
        <tr>
          <td>Braemar</td>
          {#each session.clans.braemar as score}
            <td>
              <input type="number" bind:value={score} />
            </td>
          {/each}
        </tr>
        <!-- Doune -->
        <tr>
          <td>Doune</td>
          {#each session.clans.doune as score}
            <td>
              <input type="number" bind:value={score} />
            </td>
          {/each}
        </tr>
        <!-- Dunvegan -->
        <tr>
          <td>Dunvegan</td>
          {#each session.clans.dunvegan as score}
            <td>
              <input type="number" bind:value={score} />
            </td>
          {/each}
        </tr>
        <!-- Glamis -->
        <tr>
          <td>Glamis</td>
          {#each session.clans.glamis as score}
            <td>
              <input type="number" bind:value={score} />
            </td>
          {/each}
        </tr>
        <!-- Sterling -->
        <tr>
          <td>Stirling</td>
          {#each session.clans.stirling as score}
            <td>
              <input type="number" bind:value={score} />
            </td>
          {/each}
        </tr>
      </tbody>
    </table>
  </div>

  <!-- Buttons -->
  <div class="field is-grouped">
    <!-- <button class="button is-success is-light" on:click={addScore}>Save</button> -->
    <button class="button is-success is-light" on:click={saveClan}>Save</button>
    <button class="button is-danger is-light">Reset</button>
  </div>

  <p>
    To completely reset the scores back to 0 on the display page, refresh (Ctrl + Shift + r or Command + r) this page (the admin page), then save the scores.
  </p>
</div>
