<script lang="ts" >
	import { onMount } from 'svelte';
    onMount(() => {
        let a = document.createElement('a') as HTMLAnchorElement
        a.href = "/naukri"
        a.click()
    })
</script>