<script lang="ts">
    import Modal from "./Modal.svelte";
    import NotCandidate from "./NotCandidate.svelte";

    let content: string = "";

    let openModal: boolean = false;
    let notCandidateOpen: boolean = false;

    let title: string = "";
    let photo: string = "";

    function getValue(input: number): string {
        ++input;
        return `${input < 10 ? "0" : ""}${input}`;
    }

    function generateArray(quantity: number): string[] {
        let array: string[] = Array(quantity).fill("0");
        return array;
    }

    const data: string[] = generateArray(40);

    for (let index = 0; index < 40; ++index) {
        content += `<div class="card__item"><img src="./images/${getValue(index)}.png" alt="" title="Foto-${getValue(index)}" /></div>`;
    }

    function handle(e: MouseEvent): void {
        const { target } = e;

        if (!(target instanceof HTMLElement)) {
            return;
        }

        const { index } = target.dataset;
        const error: boolean = index != "15" && index != "17" && index != "27";

        if (error) {
            notCandidateOpen = false;
            notCandidateOpen = true;

            return;
        }

        const img: HTMLImageElement | null = target.querySelector("img");

        if (!(img instanceof HTMLImageElement)) {
            return;
        }

        const { src, title: newTitle } = img;

        title = newTitle;
        photo = src;
        openModal = false;
        openModal = true;
    }
</script>

<div class="card">
    <div class="card__inner">
        <!-- {@html content} -->
        {#each data as { }, index}
            <!-- content here -->
            <button
                class="card__item"
                data-index={getValue(index)}
                on:click={handle}
                title={getValue(index)}
            >
                <img
                    src="./images/{getValue(index)}.png"
                    alt="Foto - {getValue(index)}"
                    title="Foto - {getValue(index)}"
                />
            </button>
        {/each}
    </div>
    <Modal open={openModal} {title} {photo} />
    <NotCandidate openModal={notCandidateOpen} />
</div>
