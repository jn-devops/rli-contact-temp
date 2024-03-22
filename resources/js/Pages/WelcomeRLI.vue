<script setup>
    import LandingLayout from '@/MyComponents/LandingLayout.vue';
    import PrimayButtons from '@/MyComponents/PrimayButtons.vue';
    import ArrowLongRight from '@/MyComponents/ArrowLongRight.vue';
    import ArrowLongLeft from '@/MyComponents/ArrowLongLeft.vue';
    import DialogModal from '@/Components/DialogModal.vue';
    import TermsCondition from '@/MyComponents/TermsCondition.vue';
    import DataPivacy from '@/MyComponents/DataPrivacy.vue';
    import { Head, Link } from '@inertiajs/vue3';
    import { ref, onMounted, onUnmounted} from 'vue';

    const showDialogModalTerms = ref(null);
    const openDialogModalTerm = () => {
        showDialogModalTerms.value = !showDialogModalTerms.value;
        showDialogModalData.value = false;
    }
    const showDialogModalData = ref(null);
    const openDialogModalData = () => {
        showDialogModalTerms.value = false;
        showDialogModalData.value = !showDialogModalData.value;
    }
</script>
<template>
    <!-- <h1>Welcome RLI</h1> -->
    <div class="h-screen">
        <LandingLayout class="h-full">
            <template #content>
                <div class="pt-4">
                    <h1 class="font-bold text-5xl">Welcome to Contact</h1>
                </div>
                <div class="pt-4 pr-4">
                    <p>Your participation is highly valued and will enhance our service to you. Please take a few moments to accurately complete the following information. You can rest assured that all the information you provide will be kept confidential and used only for the purposes specified in our privacy policy.</p>
                </div>
            </template>
            <template #buttons>
                <PrimayButtons @click="openDialogModalTerm">
                    <template #text>
                        <div class="flex justify-center items-center">
                            Start Now &nbsp;&nbsp;<ArrowLongRight />
                        </div>
                    </template>
                </PrimayButtons>
            </template>
        </LandingLayout>
    </div>
    <DialogModal :show="showDialogModalTerms" @close="openDialogModalTerm">
        <template #title>
        <div class="flex items-start gap-3 justify-between py-4">
            <div class="text-3xl font-bold">Terms & Condition</div>
            <div class="text-1xl text-gray-400 bg-gray-50 rounded-full px-2">
                <button @click="openDialogModalTerm">&times;</button>
            </div>
        </div>
        </template>
        <template #content>
            <div class="h-64 overflow-y-auto overflow-x-hidden p-4 scrollbar-thin scrollbar-thumb-gray-400 scrollbar-track-gray-200">
                <TermsCondition />
            </div>
        </template>
        <template #footer>
            <div class="grid items-end">
                <PrimayButtons 
                @click="openDialogModalData" 
                >
                    <template #text>
                        <div class="flex justify-center items-center">
                            View Data Privacy &nbsp;&nbsp;<ArrowLongRight />
                        </div>
                    </template>
                </PrimayButtons>
            </div>
        </template>
    </DialogModal>
    <DialogModal :show="showDialogModalData" @close="openDialogModalData">
        <template #title>
            <div class="flex items-start gap-3 justify-between py-4">
                <div class="text-3xl font-bold">Data Privacy</div>
                <div class="text-1xl text-gray-400 bg-gray-50 rounded-full px-2">
                    <button @click="openDialogModalData">&times;</button>
                </div>
            </div>
        </template>
        <template #content>
            <div class="h-64 overflow-y-auto overflow-x-hidden p-4 scrollbar-thin scrollbar-thumb-gray-400 scrollbar-track-gray-200">
            <!-- <TermsCondition /> -->
                <DataPivacy />
            </div>
        </template>
        <template #footer>
            <div class="grid grid-cols-2 items-end gap-3">
                <PrimayButtons 
                @click="openDialogModalTerm" 
                >
                    <template #text>
                        <div class="flex justify-center items-center">
                            <ArrowLongLeft />&nbsp;&nbsp; Terms & Condition
                        </div>
                    </template>
                </PrimayButtons>
                <Link
                :href="route('login')"
                >
                    <PrimayButtons 
                    @click="openDialogModalData" 
                    >
                        <template #text>
                            <div class="flex justify-center items-center">
                                I Agree & Continue &nbsp;&nbsp;<ArrowLongRight />
                            </div>
                        </template>
                    </PrimayButtons>
                </Link>
            </div>
        </template>
    </DialogModal>
</template>