<script setup>
import Accordion from "./components/Accordion.vue";
</script>

<template>
  <main>
    <div class="col-12">
      <!-- 
        Accordion Options:
          accordionId: is used to specific the accordion element 
            it should be unique if you have multiple accordion in one page.
          data: Accordion with dynamic data, ex. { title: "", body: ""},
          alwaysOpen: if ture, then all elemnts can be open at same time.
          firstAriaExpanded: if ture, then the first item will be opeining on the page load.
          type: Add flush to remove the default background-color, some borders, and some rounded corners to render accordions edge-to-edge with their parent container.
        -->
      <div class="form">
        <label class="form-check-label p-2">
          <input @change="updateAccordion()" type="checkbox" class="form-check-input" name="alwaysOpen" id="alwaysOpen" value="1" v-model="alwaysOpen">
          Always Open
        </label>
        <label class="form-check-label p-2">
          <input @change="updateAccordion()" type="checkbox" class="form-check-input" name="firstAriaExpanded" id="firstAriaExpanded" value="1" v-model="firstAriaExpanded">
          First Element Expanded
        </label>
        <label class="form-check-label p-2">
          <input @change="updateAccordion()" type="checkbox" class="form-check-input" name="accordionType" id="accordionType" value="flush" v-model="accordionType">
          Flush
        </label>
      </div>
      <Accordion
        :key="accordionKey"
        accordionId="ac_1"
        :data="accordionData"
        :alwaysOpen="alwaysOpen"
        :firstAriaExpanded="firstAriaExpanded"
        :type="accordionType ? 'flush' : 'default'"
      />
    </div>
  </main>
</template>
<script>
export default {
  data() {
    return {
      accordionKey: 0,
      alwaysOpen: false,
      accordionType: false,
      firstAriaExpanded: false,
      accordionData: [
        {
          title: "Accordion Item",
          body: `<strong>This is the first item's accordion body.</strong> It is shown by default, until the collapse plugin adds the appropriate classes that we use to style each element. These classes control the overall appearance, as well as the showing and hiding via CSS transitions. You can modify any of this with custom CSS or overriding our default variables. It's also worth noting that just about any HTML can go within the <code>.accordion-body</code>, though the transition does limit overflow.`,
        },
        {
          title: "Accordion Item",
          body: `<strong>This is the first item's accordion body.</strong> It is shown by default, until the collapse plugin adds the appropriate classes that we use to style each element. These classes control the overall appearance, as well as the showing and hiding via CSS transitions. You can modify any of this with custom CSS or overriding our default variables. It's also worth noting that just about any HTML can go within the <code>.accordion-body</code>, though the transition does limit overflow.`,
        },
        {
          title: "Accordion Item",
          body: `<strong>This is the first item's accordion body.</strong> It is shown by default, until the collapse plugin adds the appropriate classes that we use to style each element. These classes control the overall appearance, as well as the showing and hiding via CSS transitions. You can modify any of this with custom CSS or overriding our default variables. It's also worth noting that just about any HTML can go within the <code>.accordion-body</code>, though the transition does limit overflow.`,
        },
        {
          title: "Accordion Item",
          body: `<strong>This is the first item's accordion body.</strong> It is shown by default, until the collapse plugin adds the appropriate classes that we use to style each element. These classes control the overall appearance, as well as the showing and hiding via CSS transitions. You can modify any of this with custom CSS or overriding our default variables. It's also worth noting that just about any HTML can go within the <code>.accordion-body</code>, though the transition does limit overflow.`,
        },
        {
          title: "Accordion Item",
          body: `<strong>This is the first item's accordion body.</strong> It is shown by default, until the collapse plugin adds the appropriate classes that we use to style each element. These classes control the overall appearance, as well as the showing and hiding via CSS transitions. You can modify any of this with custom CSS or overriding our default variables. It's also worth noting that just about any HTML can go within the <code>.accordion-body</code>, though the transition does limit overflow.`,
        },
      ],
    };
  },
  methods: {
    updateAccordion(){
      this.accordionKey +=1;
    }
  },
};
</script>
<style>
@import "./assets/base.css";

#app {
  max-width: 1280px;
  margin: 0 auto;
  padding: 2rem;

  font-weight: normal;
}

header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

a,
.green {
  text-decoration: none;
  color: hsla(160, 100%, 37%, 1);
  transition: 0.4s;
}

@media (hover: hover) {
  a:hover {
    background-color: hsla(160, 100%, 37%, 0.2);
  }
}

@media (min-width: 1024px) {
  body {
    display: flex;
    place-items: center;
  }

  #app {
    display: grid;
    grid-template-columns: 1fr 1fr;
    padding: 0 2rem;
  }

  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }

  .logo {
    margin: 0 2rem 0 0;
  }
}
</style>
