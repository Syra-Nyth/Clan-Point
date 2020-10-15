<script>
  import Nav from './_components/Nav.svelte'

  // create an empty clan object
  let clan = {
    clanName: "",
    athletics: "",
    swimmingSports: "",
    rangiRoadie: "",
    clanQuiz: "",
    crossCountry: "",
    clanSinging: ""
  }

  function saveClan() {
    console.log("saveClan() clicked");
    // save the person object to the database under their first name
    db.collection("clans")
      .doc(clan.clanName)
      .set(clan);
  }

  async function getClan() {
    // get the document from the database for the given clan
    let clanDoc = await db
      .collection("clans")
      .doc(clan.clanName)
      .get();

    // get the data from the person document
    clan = clanDoc.data();
  }

  getClan()

</script>

<Nav />
<!-- this is just a section to make the page look nice -->
<section class="content section">

  <h1>Clans</h1>

  <!-- a place to enter the Clan name -->
  <label>
    Clan:
    <input bind:value={clan.clanName} />
  </label>

  <!-- a place to enter the Athletics Results -->
  <label>
    Athletics:
    <input bind:value={clan.athletics} />
  </label>

  <!-- a place to enter the Swimming Sports Results -->
  <label>
    Swimming Sports:
    <input bind:value={clan.swimmingSports} />
  </label>

  <button on:click={getClan}>Get Clan</button>
  <button on:click={saveClan}>Save Clan</button>

</section>
