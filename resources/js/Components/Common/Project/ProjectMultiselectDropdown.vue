<script setup lang="ts">
import MultiselectDropdown from '@/Components/Common/MultiselectDropdown.vue';
import { storeToRefs } from 'pinia';
import { useProjectsStore } from '@/utils/useProjects';
import type { Project } from '@/utils/api';

const projectsStore = useProjectsStore();
const { projects } = storeToRefs(projectsStore);

function getKeyFromItem(item: Project) {
    return item.id;
}

function getNameForItem(item: Project) {
    return item.name;
}
</script>

<template>
    <MultiselectDropdown
        searchPlaceholder="Search for a Project..."
        :items="projects"
        :get-key-from-item="getKeyFromItem"
        :get-name-for-item="getNameForItem">
        <template #trigger>
            <slot name="trigger"></slot>
        </template>
    </MultiselectDropdown>
</template>
