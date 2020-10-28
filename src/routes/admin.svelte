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
    // if ((holdScores = isNaN()) === true) {
    //   alert("You have left an input empty")
    // } else {  
      // Rounds down any decimal places in the clan data
      session.clans.balmoral.forEach((num, index) => {
        console.log(`balmoral score before: ${num}`)
        session.clans.balmoral[index] = parseInt(num)
        console.log(`balmoral score after: ${num}`)
      })

      // Rounds down any decimal places in the clan data
      session.clans.braemar.forEach((num, index) => {
        console.log(`braemar score before: ${num}`)
        session.clans.braemar[index] = parseInt(num)
        console.log(`braemar score after: ${num}`)
      })

      // Rounds down any decimal places in the clan data
      session.clans.doune.forEach((num, index) => {
        console.log(`doune score before: ${num}`)
        session.clans.doune[index] = parseInt(num)
        console.log(`doune score after: ${num}`)
      })

      // Rounds down any decimal places in the clan data
      session.clans.dunvegan.forEach((num, index) => {
        console.log(`dunvegan score before: ${num}`)
        session.clans.dunvegan[index] = parseInt(num)
        console.log(`dunvegan score after: ${num}`)
      })

      // Rounds down any decimal places in the clan data
      session.clans.glamis.forEach((num, index) => {
        console.log(`glamis score before: ${num}`)
        session.clans.glamis[index] = parseInt(num)
        console.log(`glamis score after: ${num}`)
      })

      // Rounds down any decimal places in the clan data
      session.clans.stirling.forEach((num, index) => {
        console.log(`stirling score before: ${num}`)
        session.clans.stirling[index] = parseInt(num)
        console.log(`stirling score after: ${num}`)
      })

      console.log("saveClan() clicked");
      // save the clan placings to the database under the clan name
      console.log(session.clans);
      db.collection("clans")
        .doc("placings")
        .set(session.clans);

      let clanDoc = db
        .collection("clans")
        .doc("placings")
        .get();

      alert("Clan placings saved!");
    // }
  }

  // fetches the clan placings from the database
  async function getClan() {
    // get the document from the database for all clans
    let clanDoc = await db
      .collection("clans")
      .doc("placings")
      .get();

    // get the data from the clan document
    holdScores = clanDoc.data();

    // replaces any changes not saved with what is in the database
    session.clans = holdScores;
  }

  // runs the getClan function when the webpage loads
  getClan();

  /*If the session.clans data is not found (is 'falsey'), then this data will be used a placeholder for the table until the correct data can be inserted.*/
  if (!session.clans) {
    session.clans = {
      balmoral: [0, 0, 0, 0, 0, 0, 0, 0],
      braemar: [0, 0, 0, 0, 0, 0, 0, 0],
      doune: [0, 0, 0, 0, 0, 0, 0, 0],
      dunvegan: [0, 0, 0, 0, 0, 0, 0, 0],
      glamis: [0, 0, 0, 0, 0, 0, 0, 0],
      stirling: [0, 0, 0, 0, 0, 0, 0, 0]
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
          <td>Clan Hat</td>
          <td>Swimming Sports</td>
          <td>Rangi Roadie</td>
          <td>Clan Quiz</td>
          <td>Clan Singing</td>
          <td>Total</td>
        </tr>
        <!-- Balmoral -->
        <tr>
          <td>Balmoral</td>
          <!-- prints each number in the clan document as a cell in the table -->
          {#each session.clans.balmoral as score}
            <td>
              <input type="number" max="6" min="0" maxlength="1" bind:value={score} />
            </td>
          {/each}
        </tr>
        <!-- Braemar -->
        <tr>
          <td>Braemar</td>
          <!-- prints each number in the clan document as a cell in the table -->
          {#each session.clans.braemar as score}
            <td>
              <input type="number" max="6" min="0" bind:value={score} />
            </td>
          {/each}
        </tr>
        <!-- Doune -->
        <tr>
          <td>Doune</td>
          <!-- prints each number in the clan document as a cell in the table -->
          {#each session.clans.doune as score}
            <td>
              <input type="number" max="6" min="0" bind:value={score} />
            </td>
          {/each}
        </tr>
        <!-- Dunvegan -->
        <tr>
          <td>Dunvegan</td>
          <!-- prints each number in the clan document as a cell in the table -->
          {#each session.clans.dunvegan as score}
            <td>
              <input type="number" max="6" min="0" bind:value={score} />
            </td>
          {/each}
        </tr>
        <!-- Glamis -->
        <tr>
          <td>Glamis</td>
          <!-- prints each number in the clan document as a cell in the table -->
          {#each session.clans.glamis as score}
            <td>
              <input type="number" max="6" min="0" bind:value={score} />
            </td>
          {/each}
        </tr>
        <!-- Sterling -->
        <tr>
          <td>Stirling</td>
          <!-- prints each number in the clan document as a cell in the table -->
          {#each session.clans.stirling as score}
            <td>
              <input type="number" max="6" min="0" bind:value={score} />
            </td>
          {/each}
        </tr>
      </tbody>
    </table>
  </div>

  <!-- Buttons -->
  <div class="field is-grouped">
    <button class="button is-success is-light" on:click={saveClan}>Save</button>
    <button class="button is-danger is-light" on:click={getClan}>Reset</button>
  </div>

</div>
