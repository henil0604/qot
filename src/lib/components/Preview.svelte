<script lang="ts">
    export let text = "";
</script>

<div class="w-[300px] md:w-[500px] aspect-[9/16] mockup-phone mx-0">
    <div class="camera" />
    <div class="display w-full h-full overflow-hidden">
        <div class="artboard w-full h-full artboard-demo phone-0">
            <div
                id="preview"
                class="min-w-full min-h-full bg-white text-black italic flex-center font-semibold px-4 break-words text-xs"
            >
                "{text}"
            </div>
        </div>
    </div>
</div>
