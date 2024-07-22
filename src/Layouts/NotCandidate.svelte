<script lang="ts">
    export let openModal: boolean = false;

    function handle(): void {
        openModal = false;
    }
</script>

{#if openModal}
    <div class="modal-container">
        <section class="modal">
            <div class="modal__container">
                <div>
                    <h2 class="modal__title modal__title--error">
                        El candidato seleccionado no es el adecuado
                    </h2>
                    <p class="text text--center">
                        Por una Venezuela mejor, elige al candidato correcto.
                    </p>
                </div>
            </div>

            <footer class="modal__footer">
                <button class="button button--close" on:click={handle}
                    >Cerrar</button
                >
            </footer>
        </section>
    </div>
{/if}

<style>
    .text {
        text-align: var(--align);
    }

    .text--center {
        --align: center;
    }
</style>
