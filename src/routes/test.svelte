<script>
  import Nav from './_components/Nav.svelte'

  // create an empty clan object
  let events = {
    clanName: "",
    athletics: "",
    swimmingSports: "",
    rangiRoadie: "",
    clanQuiz: "",
    crossCountry: "",
    clanSinging: "",
    total: ""
  }

  let clans = {
    balmoral: "",
    braemar: "",
    doune: "",
    dunvegan: "",
    glamis: "",
    stirling: ""
  }

  // if (clans.length > 0) {
  //   let n = 6

  //   session.clans.{clans}.forEach((num, index) => {
  //   console.log(`${clans} score before: ${num}`)
  //   session.clans.{clans}[index] = parseInt(num)
  //   console.log(`${clans} score after: ${num}`)
  //   })

  //   n = n - 1

  // }
  

</script>

  <tr id="title">
    <td class="clan">Clan</td>
    {#each events as event}
    <td>{event}</td>
    {/each}
  </tr>

  <!-- {#each clans as clan}
    <tr>
      <td>{clan}</td>
      <!-- prints each number in the clan document as a cell in the table -->
      <!-- {#each session.clans.clan as score}
        <td>
          <input type="number" max="6" min="0" bind:value={score} />
        </td>
      {/each}
    </tr>
  {/each} -->