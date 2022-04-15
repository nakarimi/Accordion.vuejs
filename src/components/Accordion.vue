<!-- 
Accordion Options:
  accordionId: is used to specific the accordion element 
    it should be unique if you have multiple accordion in one page.
  data: Accordion with dynamic data, ex. { title: "", body: ""},
  alwaysOpen: if ture, then all elemnts can be open at same time.
  firstAriaExpanded: if ture, then the first item will be opeining on the page load.
  type: Add flush to remove the default background-color, some borders, and some rounded corners to render accordions edge-to-edge with their parent container.
-->
<template>
<div class="accordion-wrapper" :class="type">
  <div :class="{ 'accordion-flush': type === 'flush' }" class="accordion row p-0" :id="accordionId">
  
    <!-- Loop over list of accordion items -->
    <div class="accordion-item p-0" v-for="(item, index) in data" :key="index">
      <h2 class="accordion-header" id="headingOne">
        <button class="accordion-button" :class="{ collapsed: !(index == 0 && firstAriaExpanded == true) }" type="button" data-bs-toggle="collapse" :data-bs-target="'#' + accordionId + index" aria-expanded="false" :aria-controls="accordionId + index">
          {{ item.title }} #{{ index + 1 }}
        </button>
      </h2>
      <div :id="accordionId + index" class="accordion-collapse collapse" :class="{ show: index == 0 && firstAriaExpanded == true }" aria-labelledby="headingOne" :data-bs-parent="alwaysOpen == false ? '#' + accordionId : null">
        <div class="accordion-body">
          <span v-html="item.body"></span>
        </div>
      </div>
    </div>
  </div>
</div>
</template>

<script setup>
defineProps({
  type: {
    type: String,
    required: false,
    default: "default",
  },
  alwaysOpen: {
    type: Boolean,
    default: false,
    required: false,
  },
  firstAriaExpanded: {
    type: Boolean,
    default: false,
    required: false,
  },
  accordionId: {
    type: String,
    required: true,
  },
  data: {
    type: Object,
    required: true,
  },
});
</script>
