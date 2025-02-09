<script lang="ts">
import { onMount } from 'svelte';
    onMount(() => {
        let a = document.createElement('a') as HTMLAnchorElement
        a.href = "/naukri/home"
        a.click()
    })
</script>
<div>
    <p>Naukri Loading...</p>
</div>
<style>
    div{
        width: 100%;
        height: 100%;
        display: flex;
        align-items: center;
        justify-content: center;
    }
</style>