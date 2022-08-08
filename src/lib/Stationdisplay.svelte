<script>

    export let data
    
    const items = {
        temperature: {
            title: 'Actuele temperatuur',
            icon: '<?xml version="1.0" encoding="utf-8"?><svg version="1.1" id="Icons" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" x="0px" y="0px" viewBox="0 0 32 32" style="enable-background:new 0 0 32 32;" xml:space="preserve"><style type="text/css">	.st0{fill:none;stroke:#000000;stroke-width:2;stroke-linecap:round;stroke-linejoin:round;stroke-miterlimit:10;} .st1{fill:none;stroke:#000000;stroke-width:2;stroke-linejoin:round;stroke-miterlimit:10;}</style><path class="st0" d="M19,17.81V6c0-1.66-1.34-3-3-3s-3,1.34-3,3v11.81c-1.79,1.04-3,2.97-3,5.19c0,3.31,2.69,6,6,6s6-2.69,6-6 C22,20.78,20.79,18.85,19,17.81z"/><circle class="st0" cx="16" cy="23" r="3"/><line class="st0" x1="16" y1="13" x2="16" y2="20"/></svg>'
        },
        sunpower: {
            title: 'Zonnekracht',
            icon: '<?xml version="1.0" encoding="utf-8"?><svg version="1.1" id="Icons" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" x="0px" y="0px" viewBox="0 0 32 32" style="enable-background:new 0 0 32 32;" xml:space="preserve"><style type="text/css">	.st0{fill:none;stroke:#000000;stroke-width:2;stroke-linecap:round;stroke-linejoin:round;stroke-miterlimit:10;}	.st1{fill:none;stroke:#000000;stroke-width:2;stroke-linejoin:round;stroke-miterlimit:10;}</style><circle class="st0" cx="16" cy="16" r="7"/><line class="st0" x1="16" y1="3" x2="16" y2="6"/><line class="st0" x1="6.81" y1="6.81" x2="8.93" y2="8.93"/><line class="st0" x1="3" y1="16" x2="6" y2="16"/><line class="st0" x1="6.81" y1="25.19" x2="8.93" y2="23.07"/><line class="st0" x1="16" y1="29" x2="16" y2="26"/><line class="st0" x1="25.19" y1="25.19" x2="23.07" y2="23.07"/><line class="st0" x1="29" y1="16" x2="26" y2="16"/><line class="st0" x1="25.19" y1="6.81" x2="23.07" y2="8.93"/></svg>'
        },
        feeltemperature: {
            title: 'Gevoelstemperatuur',
            icon: '<?xml version="1.0" encoding="utf-8"?><svg version="1.1" id="Icons" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" x="0px" y="0px" viewBox="0 0 32 32" style="enable-background:new 0 0 32 32;" xml:space="preserve"><style type="text/css">	.st0{fill:none;stroke:#000000;stroke-width:2;stroke-linecap:round;stroke-linejoin:round;stroke-miterlimit:10;} .st1{fill:none;stroke:#000000;stroke-width:2;stroke-linejoin:round;stroke-miterlimit:10;}</style><path class="st0" d="M15,17.81V6c0-1.66-1.34-3-3-3S9,4.34,9,6v11.81C7.21,18.85,6,20.78,6,23c0,3.31,2.69,6,6,6s6-2.69,6-6 C18,20.78,16.79,18.85,15,17.81z"/><circle class="st0" cx="12" cy="23" r="3"/><line class="st0" x1="12" y1="13" x2="12" y2="20"/><line class="st0" x1="20" y1="6" x2="25" y2="6"/><line class="st0" x1="20" y1="10" x2="22" y2="10"/><line class="st0" x1="20" y1="14" x2="25" y2="14"/><line class="st0" x1="20" y1="18" x2="22" y2="18"/></svg>'
        },
        rainFallLastHour: {
            title: 'Regen laatste uur',
            icon: '<?xml version="1.0" encoding="utf-8"?><svg version="1.1" id="Icons" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" x="0px" y="0px" viewBox="0 0 32 32" style="enable-background:new 0 0 32 32;" xml:space="preserve"><style type="text/css">	.st0{fill:none;stroke:#000000;stroke-width:2;stroke-linecap:round;stroke-linejoin:round;stroke-miterlimit:10;} .st1{fill:none;stroke:#000000;stroke-width:2;stroke-linejoin:round;stroke-miterlimit:10;}</style><line class="st0" x1="16" y1="3" x2="16" y2="5"/><path class="st0" d="M16,18v8v0.5c0,1.38-1.12,2.5-2.5,2.5S11,27.88,11,26.5"/><path class="st0" d="M27,11c0,2.21-1.79,4-4,4s-4-1.79-4-4s4-8,4-8S27,8.79,27,11z"/><path class="st0" d="M21.08,6.03C19.52,5.37,17.8,5,16,5C8.82,5,3,10.82,3,18h26c0-2.45-0.68-4.75-1.86-6.71"/></svg>'
        },
        groundtemperature: {
            title: 'Grond temperatuur',
            icon: '<?xml version="1.0" encoding="utf-8"?><svg version="1.1" id="Icons" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" x="0px" y="0px"	 viewBox="0 0 32 32" style="enable-background:new 0 0 32 32;" xml:space="preserve"><style type="text/css">	.st0{fill:none;stroke:#000000;stroke-width:2;stroke-linecap:round;stroke-linejoin:round;stroke-miterlimit:10;} .st1{fill:none;stroke:#000000;stroke-width:2;stroke-linejoin:round;stroke-miterlimit:10;}</style><path class="st0" d="M12,17.81V6c0-1.66-1.34-3-3-3S6,4.34,6,6v11.81C4.21,18.85,3,20.78,3,23c0,3.31,2.69,6,6,6s6-2.69,6-6 C15,20.78,13.79,18.85,12,17.81z"/><circle class="st0" cx="9" cy="23" r="3"/><line class="st0" x1="9" y1="6" x2="9" y2="20"/><circle class="st0" cx="20" cy="13" r="4"/><line class="st0" x1="20" y1="4" x2="20" y2="6"/><line class="st0" x1="20" y1="22" x2="20" y2="20"/><line class="st0" x1="26.36" y1="19.36" x2="24.95" y2="17.95"/><line class="st0" x1="29" y1="13" x2="27" y2="13"/><line class="st0" x1="26.36" y1="6.64" x2="24.95" y2="8.05"/></svg>'
        },
        winddirection: {
            title: 'Windrichting',
            icon: '<?xml version="1.0" encoding="utf-8"?><svg version="1.1" id="Icons" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" x="0px" y="0px" viewBox="0 0 32 32" style="enable-background:new 0 0 32 32;" xml:space="preserve"><style type="text/css"> .st0{fill:none;stroke:#000000;stroke-width:2;stroke-linecap:round;stroke-linejoin:round;stroke-miterlimit:10;} .st1{fill:none;stroke:#000000;stroke-width:2;stroke-linejoin:round;stroke-miterlimit:10;} </style><line class="st0" x1="5" y1="3" x2="5" y2="29"/><g><path class="st0" d="M27,14.38c-6.8,3.75-10.2-0.52-17,3.23c0-4.4,0-6.6,0-11c6.8-0.55,10.2,5.32,17,4.77 C27,12.58,27,13.18,27,14.38z"/></g><line class="st0" x1="10" y1="7" x2="5" y2="11"/><line class="st0" x1="5" y1="13" x2="10" y2="17"/><line class="st0" x1="14" y1="7.03" x2="14" y2="16.15"/><line class="st0" x1="18" y1="8.74" x2="18" y2="15.98"/><line class="st0" x1="22" y1="10.64" x2="22" y2="16"/></svg>'
        }
    }

</script>

<h2><a href='/{data.stationname}'>{data.stationname}</a></h2>
<div class="station">
    {#each Object.keys(items) as item}
        {#if data[item] || data[item] === 0}
            <div class="stats">
                <div class="icon">{@html items[item].icon}</div>
                <div class="stat">{data[item]}</div>
                <div class="title">{items[item].title}</div>
            </div>
        {/if}
    {/each}
</div>

<style>
    
    h2 {
        font-size: 1rem;
        background-color: white;
    }
    h2::after {
        content: '';
        position: relative;
        background-color: rgba(0,0,0,.2);
        display: block;
        height: 2px;
        width: 100%;
        max-width: 768px;
        margin: auto;
    }
    .station {
        display: grid;
        grid-template-columns: 50% 50%;
        row-gap: 20px;
        margin: auto;
    }
    .stats {
        display: grid;
        grid-template-areas: "icon stat"
                             "icon title";
        grid-template-columns: 50px auto;
        width: 140px;
    }
    .stats:nth-of-type(odd) {
        margin-right: 20px;
    }
    .stats:nth-of-type(even) {
        margin-left: 20px;
        justify-self: end;
    }
    .icon {
        grid-area: icon;
        display: flex;
        align-items: center;
    }
    .stat {
        font-weight: bold;
        color: #4ad6ed;
        grid-area: stat;
        text-align: end;
    }
    .title {
        font-weight: bold;
        font-size: .5rem;
        grid-area: title;
        text-align: end;
    }
    @media (min-width: 600px) {
        .station {
            max-width: 768px;
            grid-template-columns: 33% 33% 33%;
        }
        .stats:nth-of-type(odd) {
            margin-right: 0;
        }
        .stats:nth-of-type(even) {
            margin-left: 0;
        }
        .stats:nth-of-type(3n+1) {
            justify-self: start;
        }
        .stats:nth-of-type(3n+2) {
            justify-self: center;
        }
        .stats:nth-of-type(3n+3) {
            justify-self: end;
        }
    }

</style>