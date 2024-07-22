<script lang="ts">
    import Notification from "./Notification.svelte";

    export let open: boolean = false;
    export let photo: string;
    export let title: string;

    let openNotification: boolean = false;

    function handle(): void {
        open = false;
        openNotification = true;

        setTimeout(() => {
            openNotification = false;
        }, 4000);
    }
</script>

{#if open}
    <div class="modal-container">
        <section class="modal">
            <header class="modal__header">
                <h2 class="modal__title">
                    Verifique su selección y presione VOTAR
                </h2>
            </header>
            <div class="modal__container">
                <img src={photo} alt={title} {title} />
            </div>
            <footer class="modal__footer">
                <button class="button button--vote" on:click={handle}>
                    VOTAR
                </button>
            </footer>
        </section>
    </div>
{/if}

<Notification open={openNotification} />
