<template>
    <div class="grid md:grid-cols-2">
        <div class="h-auto grid items-center p-8">
            <div class="p-10">
                <div class="">
                    <img src="../../img/RLI_logo.png" alt="RLI_Logo" class="h-40">
                </div>
                <div v-if="$slots.content">
                    <slot name="content" />
                </div>
                <div v-if="$slots.buttons">
                    <slot name="buttons" />
                </div>
            </div>
        </div>
        <div class="">
            <img src="../../img/Welcome_img.png" alt="Welcome_img" class="">
        </div>
    </div>
</template>