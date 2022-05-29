<script lang="ts">
    export let errorTitle: string;
    export let errorPicture: string;
    export let errorBody: string;
</script>

<svelte:head>
    <title>{ errorTitle }</title>
</svelte:head>

<div class='error'>

    <img src={errorPicture} alt={errorBody}/>

</div>