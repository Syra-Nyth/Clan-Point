<script>
  import Nav from "./_components/Nav.svelte";
  /* import Header from './_components/Header.svelte' */
  import { stores } from "@sapper/app";
  const { session } = stores();

  /*If the session.clans data, imported from the admin page, is not found (is 'falsey'), then this data will be used a placeholder for the table until the correct data can be inserted.*/
  if (!session.clans) {
    session.clans = {
      balmoral: [1, 1, 1, 1, 1, 1, 1, 1],
      braemar: [1, 1, 1, 1, 1, 1, 1, 1],
      doune: [1, 1, 1, 1, 1, 1, 1, 1],
      dunvegan: [1, 1, 1, 1, 1, 1, 1, 1],
      glamis: [1, 1, 1, 1, 1, 1, 1, 1],
      stirling: [1, 1, 1, 1, 1, 1, 1, 1]
    };
  }

  async function getClan() {
    // get the document from the database for the given clan
    let clanDoc = await db
      .collection("clans")
      .doc("placings")
      .get();

    // get the data from the person document
    session.clans = clanDoc.data();
  }

  getClan();
</script>

<style>
  div {
    background-image: url("rainbow3.png");
    background-size: 100%;
    padding-top: 50px;
    padding-bottom: 80px;
  }

  h1 {
    width: fit-content;
    margin: 0 auto;
    color: white;
    text-shadow: 0 0 5px black;
    font-size: 4em;
  }

  table {
    margin-left: auto;
    margin-right: auto;
    margin-top: 100px;
    margin-bottom: 110px;
  }

  td {
    text-align: center !important;
  }

  #title {
    background-color: #bfbfbf;
    font-weight: 500;
  }

  .clan {
    background-color: #a6a6a6;
    color: #ffffff;
    font-weight: bold;
  }

  .balmoral {
    background-color: #bdd7ee;
  }
  #balmoral-row {
    background-color: #deebf7;
  }

  .braemar {
    background-color: #d9d9d9;
  }
  #braemar-row {
    background-color: #f2f2f2;
  }

  .doune {
    background-color: #c5e0b4;
  }
  #doune-row {
    background-color: #e2f0d9;
  }

  .dunvegan {
    background-color: #ccccff;
  }
  #dunvegan-row {
    background-color: #e1e1ff;
  }

  .glamis {
    background-color: #ff9999;
  }
  #glamis-row {
    background-color: #ffcccc;
  }

  .stirling {
    background-color: #ffe699;
  }
  #stirling-row {
    background-color: #fff2cc;
  }
</style>

<!-- Table -->
<div>

  <br />

  <Nav />

  <h1 class="title is-1">Clan Points</h1>

  <table class="table is-bordered">
    <tbody>
      <!-- Title -->
      <tr id="title">
        <td class="clan">Clan</td>
        <td>400m</td>
        <td>Athletics</td>
        <td>Clan Hat</td>
        <td>Swimming Sports</td>
        <td>Rangi Roadie</td>
        <td>Clan Quiz</td>
        <td>Clan Singing</td>
        <td class="clan">Total</td>
      </tr>
      <!-- Balmoral -->
      <tr id="balmoral-row">
        <td class="balmoral">Balmoral</td>
        <!-- Takes the data from session.clans.balmoral and inputs it in the Balmoral row -->
        {#each session.clans.balmoral as score}
          <td>{score}</td>
        {/each}
      </tr>
      <!-- Braemar -->
      <tr id="braemar-row">
        <td class="braemar">Braemar</td>
        <!-- Takes the data from session.clans.braemar and inputs it in the Braemar row -->
        {#each session.clans.braemar as score}
          <td>{score}</td>
        {/each}
      </tr>
      <!-- Doune -->
      <tr id="doune-row">
        <td class="doune">Doune</td>
        <!-- Takes the data from session.clans.doune and inputs it in the Doune row -->
        {#each session.clans.doune as score}
          <td>{score}</td>
        {/each}
      </tr>
      <!-- Dunvegan -->
      <tr id="dunvegan-row">
        <td class="dunvegan">Dunvegan</td>
        <!-- Takes the data from session.clans.dunvegan and inputs it in the Dunvegan row -->
        {#each session.clans.dunvegan as score}
          <td>{score}</td>
        {/each}
      </tr>
      <!-- Glamis -->
      <tr id="glamis-row">
        <td class="glamis">Glamis</td>
        <!-- Takes the data from session.clans.glamis and inputs it in the Glamis row -->
        {#each session.clans.glamis as score}
          <td>{score}</td>
        {/each}
      </tr>
      <!-- Sterling -->
      <tr id="stirling-row">
        <td class="stirling">Stirling</td>
        <!-- Takes the data from session.clans.stirling and inputs it in the Stirling row -->
        {#each session.clans.stirling as score}
          <td>{score}</td>
        {/each}
      </tr>
    </tbody>
  </table>

</div>
