<template>
  <v-list style="overflow-y: auto" max-height="300">
    <div
      v-for="(जानकारी, index) in जानकारियाँ"
      :key="जानकारी.पहचान"
    >
      <div
        @click="toggleExpand(index)"
        style="cursor: pointer; font-weight: bold; color: black"
      >
        {{ जानकारी.गायक }}
      </div>
      <div v-if="expandedIndex === index" style="padding-left: 10px;">
        <p>{{ जानकारी.गाना }}</p>
        <p>{{ जानकारी.तिथी }}</p>
      </div>
    </div>
  </v-list>
</template>

<script setup lang="ts">
import { ref } from "vue";
import type { जानकारी_प्रकार } from "../प्रकार.ts";

const जानकारियाँ: जानकारी_प्रकार[] = [
  { गायक: "बॉम्बे जयश्री", गाना: "ममता से भरी", तिथी: "१५/१२/२०२४", पहचान: "०००१" },
  { गायक: "कैलाश खेर", गाना: "जल रहीं हैं", तिथी: "१५/१२/२०२४", पहचान: "०००२" },
  { गायक: "बॉम्बे जयश्री", गाना: "स्वप्न सुनहरा", तिथी: "१५/१२/२०२४", पहचान: "०००३" },
  { गायक: "नीति मोहन", गाना: "खोया हैं", तिथी: "१५/१२/२०२४", पहचान: "०००४" },
  { गायक: "कैलाश खेर", गाना: "कौन है वो", तिथी: "१५/१२/२०२४", पहचान: "०००५" },
 ];

const expandedIndex = ref<number | null>(null);

const toggleExpand = (index: number) => {
  expandedIndex.value = expandedIndex.value === index ? null : index;
};
</script>
