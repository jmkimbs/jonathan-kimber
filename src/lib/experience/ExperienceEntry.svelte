<script lang='ts'>
import { is_empty } from "svelte/internal";


    export let title: string;
    export let location: string;
    export let startDate: Date;
    export let endDate: Date;
    export let achievements: any;

</script>


<div class='experience-entry'>

    {#if title.length > 0}
        <h1>{title}</h1>
    {/if}

    {#if location.length > 0}
        <span class='location'>{location}</span>
    {/if}

    <span class='duration'>From {startDate.toLocaleDateString()} until {endDate.toLocaleDateString()}</span>
    <!-- {#if startDate} -->

</div>

<style>

    .experience-entry {
        border-radius: 10px;
        border: 0.1em solid black;
        padding: 0.25em 1em 1em 1em;
        display: flex;
        flex-direction: column;
    }

    .experience-entry h1 {
        text-align: left;
        font-size: 1.25em;
        display: flex;
    }

    .experience-entry span {
        display: flex;
    }

    .experience-entry .location {

    }




</style>