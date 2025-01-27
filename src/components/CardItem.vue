<script setup>
import StarRating from "vue-star-rating";

const props = defineProps({
  itemData: {
    require: true,
  },
});
</script>

<template>
  <div class="w-full h-full px-1 flex items-center">
    <div
      class="border flex items-start justify-between bg-white border-gray-300 p-2 w-full h-full"
    >
      <div>
        <div class="flex items-center gap-1 font-semibold">
          <star-rating
            class="flex items-center justify-center mb-2"
            v-model="rating"
            :star-size="20"
            :max-rating="1"
            :show-rating="false"
          ></star-rating>

          <p class="text-base text-gray-700">{{ itemData.name }}</p>
        </div>

        <p class="text-gray-600">[CONS_0001]</p>
        <div
          class="flex gap-2 flex-wrap mt-2 font-semibold"
          v-if="itemData.legs || itemData.color"
        >
          <p
            v-if="itemData.legs"
            :style="`background-color:${itemData.colorLegs}; color:${itemData.colorTextLegs}`"
            :class="`  rounded-xl px-2 text-[13px]`"
          >
            Legs: {{ itemData.legs }}
          </p>
          <p
            v-if="itemData.color"
            :style="`background-color:${itemData.bgColor}; color:${itemData.textColor}`"
            :class="`    rounded-xl px-2 text-[13px]`"
          >
            Color: {{ itemData.color }}
          </p>
        </div>

        <p class="text-sm mt-2 text-gray-600">
          Price: ${{ itemData.price.toFixed(2) }}
        </p>
      </div>

      <img class="w-14 object-contain" :src="itemData.image || ``" alt="" />
    </div>
  </div>
</template>
