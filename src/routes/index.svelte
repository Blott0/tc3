<script context="module">

// load function runs before the component is created
// retrieves weather data from buienradar.nl then reorganizes and returns it
export async function load({ params, fetch, session, stuff }) {
    const res = await fetch(`http://localhost:3001`)
    const data = await res.json()

    // reorganize data by station
    const stations = {}
    
    // for each weatherstation
    for (let i = 0; i < data.length; i++) {

      // if the stationname doesnt exist
      if (Object.keys(stations).indexOf(data[i].stationname) === -1) {
        
        // create the new station
        stations[data[i].stationname] = {}
      }

      // add current station to current region
      stations[data[i].stationname][data[i].stationname] = data[i]
    }

    return {
      props: { stations: stations }
    }
}

</script>

<script>

export let stations

// imports simple station data displayer
import Stationdisplay from '$lib/Stationdisplay.svelte'

// user selected region or 0
let selection

</script>

  <!-- dropdown for user to select region -->
  <select bind:value={selection}>
    <option disabled value=0>-- selecteer een regio --</option>
    {#each Object.keys(stations).sort() as region}
      <option value="{region}">{region}</option>
    {/each}
  </select>

  <!-- if a selection is made -->
  {#if selection && selection != 0}
    <!-- for each station in selected region -->
    {#each Object.keys(stations[selection]) as station}
      <!-- list all available data -->
      <Stationdisplay data={stations[selection][station]} />
    {/each}
  {/if}

<style>

select {
  font-size: 1.2rem;
}

</style>