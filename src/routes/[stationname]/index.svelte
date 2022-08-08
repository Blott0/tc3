<script context="module">

    export async function load({ params, fetch, session, stuff }) {
        
        const res = await fetch(`http://localhost:3001/` + params.stationname)
        const dataArray = await res.json()
    
        return {
          props: { dataArray: dataArray }
        }
    }
    
</script>
    
<script>
    
    export let dataArray

    import Stationdisplay from '$lib/Stationdisplay.svelte'

    const currDate = Date.parse(new Date())
    const defaultPeriod = 1000 * 60 * 60 * 24 * 7

</script>

<a href="/{dataArray[0].stationname}/details?startDate={currDate - defaultPeriod}&endDate={currDate}">details</a>
{#each dataArray as data}
    <Stationdisplay {data} />
{/each}