<script setup>
import StarRating from "vue-star-rating";
import { Star } from "lucide-vue-next";
import { ref } from "vue";
const props = defineProps({
  itemData: {
    require: true,
  },
});

const star = ref(false);
function handleStar() {
  star.value = !star.value;
}
</script>

<template>
  <div class="w-full h-full px-1 flex items-center">
    <div
      class="border flex h-full p-2 items-start justify-between bg-white border-gray-300 w-full"
    >
      <div class="flex flex-col gap-[1px]">
        <div class="flex items-center gap-1 font-semibold">
          <Star
            @click="handleStar"
            class="w-4 h-4 hover:fill-amber-300 hover:text-amber-300 cursor-pointer"
            :class="star ? 'text-amber-300 fill-amber-300' : 'text-[#b7bbc1]'"
          />

          <p class="text-[15.4px] text-[#212529]">{{ itemData.name }}</p>
        </div>

        <p class="text-[#495057] text-[14px]">[CONS_0001]</p>
        <div
          class="flex gap-2 flex-wrap font-semibold"
          v-if="itemData.legs || itemData.color"
        >
          <p
            v-if="itemData.legs"
            :style="`background-color:${itemData.colorLegs}; color:${itemData.colorTextLegs}`"
            :class="`  rounded-xl px-2  text-[11.9px]`"
          >
            Legs: {{ itemData.legs }}
          </p>
          <p
            v-if="itemData.color"
            :style="`background-color:${itemData.bgColor}; color:${itemData.textColor}`"
            :class="`    rounded-xl px-2  text-[11.9px]`"
          >
            Color: {{ itemData.color }}
          </p>
        </div>

        <p class="text-[14px] text-[#495057]">
          Price: ${{ " " }}{{ itemData.price }}
        </p>
      </div>
      <div class="w-fit flex items-start justify-start h-full">
        <img class="w-16 object-contain" :src="itemData.image || ``" alt="" />
      </div>
    </div>
  </div>
</template>
