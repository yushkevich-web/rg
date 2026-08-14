<template>
  <div>
    <SchoolGardensPage v-if="isSchoolGardensPage" />
    <EducationalPartnersPage v-else-if="isEducationalPartnersPage" />
    <ModelCitiesPage v-else-if="isModelCitiesPage" />
    <template v-else>
      <LocalSwitcher />
      <FullScreen id="main" />
      <About id="about" />
      <Solution id="solution" />
      <Points />
      <!-- <Impact id="impact" /> -->
      <!-- <Support id="support" /> -->
      <!-- <BrownCards /> -->
      <Development id="development" />
      <Activities id="resources" />
      <Partners id="partners" />
      <Contacts />
      <Footer />
    </template>
  </div>
</template>

<script>
import LocalSwitcher from "./components/LocalSwitcher.vue";
import About from "./components/About.vue";
import FullScreen from "./components/FullScreen.vue";
import Solution from "./components/Solution.vue";
import Points from "./components/Points.vue";
import Impact from "./components/Impact.vue";
import Support from "./components/Support.vue";
import BrownCards from "./components/BrownCards.vue";
import Development from "./components/Development.vue";
import Activities from "./components/Activities.vue";
import Partners from "./components/Partners.vue";
import Contacts from "./components/Contacts.vue";
import Footer from "./components/Footer.vue";
import SchoolGardensPage from "./components/SchoolGardensPage.vue";
import EducationalPartnersPage from "./components/EducationalPartnersPage.vue";
import ModelCitiesPage from "./components/ModelCitiesPage.vue";
export default {
  components: {
    LocalSwitcher,
    FullScreen,
    About,
    Solution,
    Points,
    Impact,
    Support,
    BrownCards,
    Development,
    Activities,
    Partners,
    Contacts,
    Footer,
    SchoolGardensPage,
    EducationalPartnersPage,
    ModelCitiesPage,
  },
  data() {
    return {
      currentHash: window.location.hash,
    };
  },
  computed: {
    isSchoolGardensPage() {
      return this.currentHash === "#/school-gardens";
    },
    isEducationalPartnersPage() {
      return this.currentHash === "#/educational-partners";
    },
    isModelCitiesPage() {
      return this.currentHash === "#/model-cities";
    },
  },
  mounted() {
    if ("scrollRestoration" in window.history) {
      window.history.scrollRestoration = "manual";
    }

    window.addEventListener("hashchange", this.updateRoute);
    this.scrollToAnchor(this.currentHash);
  },
  beforeUnmount() {
    window.removeEventListener("hashchange", this.updateRoute);
  },
  methods: {
    updateRoute() {
      this.currentHash = window.location.hash;
      this.scrollToAnchor(this.currentHash);
    },
    scrollToAnchor(hash) {
      if (!hash) {
        return;
      }

      this.$nextTick(() => {
        if (hash.startsWith("#/")) {
          this.scrollPageToTop();
          return;
        }

        const target = document.querySelector(hash);

        if (target) {
          target.scrollIntoView({ behavior: "smooth", block: "start" });
        }
      });
    },
    scrollPageToTop() {
      const reset = () => {
        window.scrollTo(0, 0);
        document.documentElement.scrollTop = 0;
        document.body.scrollTop = 0;
      };

      reset();
      requestAnimationFrame(reset);
      setTimeout(reset, 50);
    },
  },
};
</script>
