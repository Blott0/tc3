<script context="module">

    export async function load({ params, url, fetch }) {
        
        const endDate = url.searchParams.get('endDate')
        const startDate = url.searchParams.get('startDate')

        const res = await fetch(`http://localhost:3001/` + params.stationname + '/details?startDate=' + startDate + '&endDate=' + endDate, {method: 'get'})
        const dataArray = await res.json()
    
        return {
          props: { dataArray: dataArray, startDate: startDate, endDate: endDate, stationName: params.stationname }
        }
    }
    
</script>
    
<script>
    
    export let dataArray
    export let startDate
    export let endDate
    export let stationName

    import Chart from 'svelte-frappe-charts'

    function convertDate(date) {
        const year = new Date(parseInt(date)).getFullYear()
        let month = new Date(parseInt(date)).getMonth() + 1
        let day = new Date(parseInt(date)).getDate()
        if (month < 10) { month = '0' + month}
        if (day < 10) { day = '0' + day}
        let dateString = year + '-' + month + '-' + day
        return dateString
    }

    let startDateParsed = convertDate(startDate)
    let endDateParsed = convertDate(endDate)

    let date = []
    let feeltemperature = []
    let groundtemperature = []
    let rainFallLastHour = []
    let sunpower = []
    let temperature = []

    $:startDateMs = Date.parse(startDateParsed)
    $:endDateMs = Date.parse(endDateParsed)
    $:newUrl = '/' + stationName + '/details?startDate=' + startDateMs + '&endDate=' + endDateMs

    dataArray.forEach(set => {
        date.push(convertDate(set.date))
        feeltemperature.push(set.feeltemperature)
        groundtemperature.push(set.groundtemperature)
        rainFallLastHour.push(set.rainFallLastHour)
        sunpower.push(set.sunpower)
        temperature.push(set.temperature)
    })

    const feeltemperatureData = {
        labels: date,
        datasets: [
            {
                values: feeltemperature
            }
        ]
    }

    const groundtemperatureData = {
        labels: date,
        datasets: [
            {
                values: groundtemperature
            }
        ]
    }

    const rainFallLastHourData = {
        labels: date,
        datasets: [
            {
                values: rainFallLastHour
            }
        ]
    }

    const sunpowerData = {
        labels: date,
        datasets: [
            {
                values: sunpower
            }
        ]
    }

    const temperatureData = {
        labels: date,
        datasets: [
            {
                values: temperature
            }
        ]
    }
    

</script>

<div>
    <label for="startDate">select start date:</label>
    <input id="startDate" type="date" bind:value="{startDateParsed}">
</div>

<div>
    <label for="endDate">select end date:</label>
    <input id="endDate" type="date" bind:value="{endDateParsed}">
</div>

<a href="{newUrl}">set new period</a>


{#if dataArray.length > 0}
    <h4>Gevoelstemperatuur</h4>
    <Chart data={feeltemperatureData} type="line" />

    <h4>Grond temperatuur</h4>
    <Chart data={groundtemperatureData} type="line" />

    <h4>Regen laatste uur</h4>
    <Chart data={rainFallLastHourData} type="line" />

    <h4>Zonnekracht</h4>
    <Chart data={sunpowerData} type="line" />

    <h4>Actuele temperatuur</h4>
    <Chart data={temperatureData} type="line" />
{:else}
    <h4>no data found in current period</h4>
{/if}
