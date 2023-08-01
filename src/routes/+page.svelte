<script lang="ts">
    import Preview from "$lib/components/Preview.svelte";
    import html2canvas from "html2canvas";

    let text = "Life is ours to be spent, not to be saved";

    function convertToSlug(text: string) {
        return text
            .toLowerCase()
            .replace(/ /g, "-")
            .replace(/[^\w-]+/g, "");
    }

    function capture() {
        html2canvas(document.querySelector("#preview") as HTMLDivElement, {
            logging: true,
        }).then((canvas) => {
            var anchorTag = document.createElement("a");
            document.body.appendChild(anchorTag);
            anchorTag.download = `${convertToSlug(text)}.jpg`;
            anchorTag.href = canvas.toDataURL();
            anchorTag.target = "_blank";
            anchorTag.click();
        });
    }
</script>

<div class="min-h-full flex-center p-3">
    <div class="flex max-md:flex-col gap-4">
        <Preview bind:text />
        <div
            class="w-full h-full flex flex-col items-start justify-start gap-4"
        >
            <div class="form-control w-full">
                <label for="" class="label">
                    <span class="label-text">Your Quote</span>
                </label>
                <input
                    type="text"
                    placeholder="Type here"
                    bind:value={text}
                    class="input input-bordered rounded-md w-full"
                />
            </div>
            <div class="w-full flex justify-end">
                <button class="btn btn-success" on:click={capture}>Save</button>
            </div>
        </div>
    </div>
    <!--  -->
</div>
