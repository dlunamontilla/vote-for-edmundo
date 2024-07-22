<script lang="ts">
    export let open: boolean = true;
</script>

{#if open}
    <div class="modal-container">
        <section class="modal">
            <div class="modal__container">
                <div>
                    <h2 class="modal__title modal__title--success">
                        El voto se ha generado correctamente
                    </h2>
                    <p>
                        Tome su comprobante y deposítelo en la caja de resguardo
                    </p>
                </div>
            </div>
        </section>
    </div>
{/if}
