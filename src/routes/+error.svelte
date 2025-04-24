<script lang="ts">
    import { page } from '$app/state'
    import Icon from '@iconify/svelte'
</script>

<section>
    <Icon icon="material-symbols:error" width="80px" />
    <h1>{page.status}: {page.error?.message}</h1>
</section>

<style>
    section {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        gap: 1rem;
        color: var(--text-color);
    }
</style>