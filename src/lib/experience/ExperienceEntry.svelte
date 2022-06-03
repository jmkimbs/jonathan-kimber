<script lang='ts'>
import { is_empty } from "svelte/internal";


    export let title: string;
    export let location: string;
    export let startDate: Date;
    export let endDate: Date;
    export let achievements: any;

</script>


<div class='experience-entry'>

    <div>
        {#if title.length > 0}
            <h1>{title}</h1>
        {/if}
    </div>
    
    <div>
        {#if location.length > 0}
            <span class='location'>{location}</span>
        {/if}
    </div>

    <div>
        <span class='duration'>From {startDate.toLocaleDateString()} until {endDate.toLocaleDateString()}</span>
    </div>
    <!-- {#if startDate} -->

</div>

<style>

    .experience-entry {
        border-radius: 20px;
        border: 0.1em solid black;
        /* padding: 0.25em 1em 1em 1em; */
        display: inline-flex;
        flex-direction: column;
        justify-content: center;
        width: fit-content;
    }

    .experience-entry div {                
        /* background-color: #f4f4f4;  */
        margin: 2px 10px 2px 10px; 
        font-size: 1em;
    }

    .experience-entry h1 {
        text-align: left;
        font-size: 1.25em;
        margin: 10px 0 5px 0;
    }

    .experience-entry div:last-of-type {
        margin-bottom: 10px;
        /* background-color: red; */
    }

    .experience-entry div span {
        /* width: auto; */
    }




</style>